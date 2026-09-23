# MEMS Offline Installation

WAGO Microgrid Energy Management System (MEMS)

This manual describes how to install, verify, update and remove MEMS on a machine
with **no internet access**.

The delivery is two files: the bundle `mems-offline-<version>.tar.gz` — every
container image, compose file, configuration template and integrity manifest —
and **one installer script, chosen by the operating system of the target host**:

| Target host | Installer script                   | Run it in                                                       |
| ----------- | ---------------------------------- | --------------------------------------------------------------- |
| **Linux**   | `install-mems.sh` (bash)           | a root shell, normally via `sudo`                                |
| **Windows** | `install-mems.ps1` (PowerShell 7+) | an **elevated** PowerShell 7 session (`pwsh` as Administrator)   |

The two scripts offer the same commands, options and exit codes, but they are not
interchangeable — use only the one that matches your platform. Everything MEMS
needs at run time is inside the bundle; the installer never contacts a registry,
a package repository or any other network service.

Every procedure below shows the **Linux** command first and the **Windows**
command directly underneath. Run only the one for your platform.

MEMS runs as a Docker Compose stack: the application, Keycloak, two PostgreSQL
databases and — optionally — Loki, Tempo, Prometheus, the OpenTelemetry
Collector, Grafana and blackbox-exporter.

---

## Contents

1. [Requirements](requirements.md)
2. [Transfer and verify the bundle](#2-transfer-and-verify-the-bundle)
3. [Install](#3-install)
4. [What the installer does for you](#4-what-the-installer-does-for-you)
5. [Finish the setup in VC Hub](#5-finish-the-setup-in-vc-hub)
6. [Check the installation](#6-check-the-installation)
7. [Update](#7-update)
8. [Uninstall](#8-uninstall)
9. [Troubleshooting](#9-troubleshooting)
10. [Configuration](#10-configuration)

---

## 1. Requirements

See [Requirements](requirements.md).

---

## 2. Transfer and verify the bundle

Both artifacts are provided by WAGO. Copy them to the
target machine on removable media or through your approved transfer path, and
put them in the **same directory**. Copy only the installer for that platform.

**Linux**

```bash
mkdir -p /var/tmp/mems-install
cd /var/tmp/mems-install
# copy mems-offline-<version>.tar.gz and install-mems.sh here
chmod +x install-mems.sh
```

**Windows (elevated PowerShell 7)**

```powershell
New-Item -ItemType Directory -Path C:\Temp\mems-install -Force
Set-Location C:\Temp\mems-install
# copy mems-offline-<version>.tar.gz and install-mems.ps1 here
Unblock-File .\install-mems.ps1
```

**Step 1 — confirm the archive is the one WAGO published.** Compare its SHA-256
with the value WAGO published for that release (the `.sha256` sidecar next to
the download). This is the step that establishes where the bundle came from.

**Linux**

```bash
sha256sum -c mems-offline-<version>.tar.gz.sha256
```

**Windows**

```powershell
$expected = (Get-Content .\mems-offline-<version>.tar.gz.sha256).Split(' ')[0]
$actual = (Get-FileHash .\mems-offline-<version>.tar.gz -Algorithm SHA256).Hash.ToLower()
if ($actual -eq $expected) { 'OK' } else { 'MISMATCH' }
```

**Step 2 — check the contents.**

**Linux**

```bash
./install-mems.sh verify --bundle ./mems-offline-<version>.tar.gz
```

**Windows**

```powershell
.\install-mems.ps1 verify --bundle .\mems-offline-<version>.tar.gz
```

`verify` checks the SHA-256 of every file inside the bundle. It also verifies the
detached signature over `SHA256SUMS`, but only when a signature is present *and*
an `openssl`-capable image is already loaded — which is not the case before the
first install. In that situation it reports that the signature was not checked
and still succeeds, so do not treat step 2 as a substitute for step 1. Run
`verify` again after the installation to include the signature check.

---

## 3. Install

### 3.1 Interactive

**Linux**

```bash
sudo ./install-mems.sh install
```

**Windows (elevated PowerShell 7)**

```powershell
.\install-mems.ps1 install
```

If exactly one `mems-offline-*.tar.gz` sits next to the script it is used
automatically. With several bundles in the directory, pass `--bundle PATH`.

The installer asks five questions and derives everything else:

| Prompt                      | Meaning                                                                 |
| --------------------------- | ----------------------------------------------------------------------- |
| Deployment hostname or IP   | The public MEMS application hostname or IP. It goes into the MEMS certificate and realm client URLs. Defaults to the primary IPv4 address of this machine. `localhost` only works for a single-machine demo. |
| Public Keycloak URL          | Complete HTTPS origin used by browsers and MEMS, for example `https://<keycloak-host>:8443`. It may use a different hostname from MEMS. |
| VC Hub base URL             | The externally reachable VC Hub URL, for example `https://<vchub-host>:10443`. |
| VC Hub OpenID client ID     | The client MEMS uses at VC Hub. Default `MEMSKeyCloak`. Register it in VC Hub under **Security → OIDC Server (Open API) → Register** with the Authorization Code Flow grant type. |
| VC Hub OpenID client secret | The corresponding secret. It is read without echo and never logged.      |

### 3.2 Unattended

`--yes` never prompts, so every value must come from an answer file — the VC Hub
client secret has no default and the install fails without it.

`mems-answers.env` (the same file works on both platforms):

```ini
# Required
DEPLOY_HOSTNAME=<hostname>
KEYCLOAK_URL=https://<keycloak-host>:8443
VC_HUB_URL=https://<vchub-host>:10443
VC_HUB_CLIENT_ID=<client-id>
VC_HUB_CLIENT_SECRET=<client-secret>

# Optional: certificate handling
#   self-signed (default) - the installer generates the reverse-proxy certificate
#   byo                   - supply your own PEM certificate and private key
CERT_MODE=self-signed

# Only for CERT_MODE=byo (PEM; the key must be unencrypted)
#TLS_CERT_SOURCE=/path/to/server.crt
#TLS_KEY_SOURCE=/path/to/server.key
```

One certificate serves every published HTTPS port, so a supplied certificate must
carry subject alternative names for both `DEPLOY_HOSTNAME` and the host in
`KEYCLOAK_URL`.

**Linux**

```bash
chmod 600 mems-answers.env
sudo ./install-mems.sh install --answers ./mems-answers.env --yes
```

**Windows** — restrict the answer file to administrators, then install:

```powershell
.\install-mems.ps1 install --answers .\mems-answers.env --yes
```

### 3.3 The initial credentials

The installer generates the PostgreSQL, Keycloak administrator, Grafana
administrator and OTLP passwords from a cryptographic random source and
stores them in the environment file. They are never written to the run log.

During an **interactive** install the Keycloak and Grafana logins are printed
once to the terminal. After an **unattended** install nothing is printed — read
them from the environment file:

**Linux**

```bash
sudo grep -E '^(KEYCLOAK_ADMIN|KEYCLOAK_ADMIN_PASSWORD|GRAFANA_ADMIN_USER|GRAFANA_ADMIN_PASSWORD)=' \
  /etc/wago/mems/mems.env
```

**Windows**

```powershell
Select-String -Path "$env:ProgramData\WAGO\MEMS\config\mems.env" `
  -Pattern '^(KEYCLOAK_ADMIN|KEYCLOAK_ADMIN_PASSWORD|GRAFANA_ADMIN_USER|GRAFANA_ADMIN_PASSWORD)='
```

Change both administrator passwords at first login.

### 3.4 Commands and options

`install-mems.sh` (Linux) and `install-mems.ps1` (Windows) expose the same
commands, options and exit codes. Run `install-mems.sh help <command>` or
`install-mems.ps1 help <command>` for the authoritative list on your platform.

- `install` — install from a bundle (the default when no command is given)
- `update` — update an existing installation, preserving configuration and data
- `uninstall` — remove MEMS; `--purge-data` also removes volumes and configuration
- `status` — show the installed version and `docker compose ps`
- `verify` — verify bundle checksums and, if possible, the signature
- `trust-vchub` — download the VC Hub certificate and add it to the truststores
- `compose-config` — print the effective Docker Compose configuration
- `compose-apply` — apply the current configuration to the running stack (`up -d`)
- `completion` — print a shell completion script
- `help` — show help, optionally for a single command

Options: `--bundle PATH`, `--answers FILE`, `--vchub-url URL`, `--hostname NAME`,
`--install-root PATH`, `--main-services-only`, `--all-services`, `--yes`,
`--force`, `--purge-data`, `--dry-run`, `--version`, `-h` / `--help`.

#### Installing only the main services

By default every service in the bundle is installed. Pass
`--main-services-only` to `install` to limit the installation to the services
MEMS cannot run without:

`postgres_mems_keycloak`, `postgres_mems_app`, `mems_keycloak`, `mems_app`,
`nginx`

The observability stack — Loki, Tempo, Prometheus, Grafana, the OpenTelemetry
Collector and blackbox-exporter — is then neither loaded nor started:

- Only `images/mems-images-main.tar` is loaded; the images in
  `images/mems-images-extra.tar` stay in the bundle and are never imported.
- The Grafana server block is removed from the nginx configuration, so the
  Grafana URL is not served and no Grafana credentials are printed.
- `mems_app` runs with `OpenTelemetry__Enabled=false`; no traces or metrics are
  exported.
- Everything else — the MEMS UI, Keycloak, VC Hub integration — is unaffected.

The choice is recorded in `state.json` and shown by `status`. `update` inherits
it, so an installation stays consistent without repeating the flag. To change
the selection later, run `update` with `--all-services` or
`--main-services-only`; the extra images are loaded from the bundle at that
point.

A bundle built before the main/extra split contains a single
`images/mems-images.tar` and declares no main service set. `--main-services-only`
still works with it — the installer warns, falls back to the built-in main
service list above, and loads every bundled image even though it starts only the
main ones.

### 3.5 Phases and what happens on failure

The run is reported in eleven phases. The one that fails names the cause:

> Preflight → Bundle discovery → Extraction and checksum verification → Loading
> container images → Configuration → Certificates → Keycloak realm → Starting the
> stack → Verifying the Keycloak realm → Activating the release → Reconciling
> images

If a phase fails during `install`, the installer stops and **keeps** the
containers, the release directory and the volumes so you can inspect them with
`docker compose ps` and `docker compose logs`. The release is not activated, so a
previously installed version stays active. Fix the cause and run `install` again.

### 3.6 Installation layout

**Linux**

| Path                                 | Contents                                      |
| ------------------------------------ | --------------------------------------------- |
| `/opt/wago/mems/releases/<version>/` | Extracted bundle payload                      |
| `/opt/wago/mems/current`             | Symlink to the active release                 |
| `/opt/wago/mems/state.json`          | Installed version, timestamp, bundle checksum |
| `/opt/wago/mems/scripts/`            | `compose-config.sh`, `compose-apply.sh`       |
| `/etc/wago/mems/mems.env`            | Environment file, mode `0600`, root-owned     |
| `/etc/wago/mems/nginx-cert/`         | `server.crt` and `server.key` used by the reverse proxy |
| `/etc/wago/mems/keycloak-truststore/`, `mems-truststore/` | Trusted CA certificates (PEM/CRT) |
| `/var/log/wago/mems/`                | Installer logs, one file per run              |

**Windows** — the same layout under `%ProgramData%\WAGO\MEMS\`, with
`releases\`, `current` (a junction), `state.json`, `scripts\`, `config\` (the
environment file and the certificate directories, readable by administrators
only) and `logs\`.

`--install-root` moves the payload only; the configuration and the logs stay at
their fixed paths. It is **not remembered** — pass the same value to `update`,
`uninstall` and `status`.

---

## 4. What the installer does for you

| Area           | Behaviour                                                                                     |
| -------------- | --------------------------------------------------------------------------------------------- |
| Images         | Loads every image from the bundle and verifies each one against the packaged inventory. Compose uses local references with `pull_policy: never`, so no registry is contacted. |
| Secrets        | Generates the PostgreSQL, Keycloak admin, Grafana admin and OTLP passwords from a cryptographic random source. Template defaults such as `rootpass` never reach a running system. |
| Certificates   | Creates one PEM certificate and key (RSA 3072, 825 days) with SANs for the deployment hostname, the Keycloak hostname, the local machine name, `localhost`, `127.0.0.1` and `::1`, using `openssl` inside the bundled PostgreSQL image. The nginx reverse proxy terminates TLS with it on every published HTTPS port. `CERT_MODE=byo` installs your own pair instead. |
| Trust stores   | Copies the reverse-proxy certificate into both trust directories so Keycloak and MEMS trust each other through the proxy. Additional CAs are picked up as PEM/CRT files from `keycloak-truststore` and `mems-truststore` — no Java truststore, no `keytool`. |
| VC Hub certificate | Downloads the VC Hub web server certificate and checks that its subject alternative names cover the host in `VC_HUB_URL`. If VC Hub is unreachable, the download fails or the names do not match, the installation stops with exit code 2 and names the mismatch, for example `Certificate for <10.160.100.46> doesn't match any of the subject alternative names: [pc-sz-fsu-1, localhost, 127.0.0.1]`. On a name mismatch an interactive run offers to generate a matching self-signed certificate; it is written as a password-protected PKCS#12 file to `vchub-cert/vchub.pfx` in the configuration directory and the password is printed to the terminal only. Upload it in VC Hub under **Node → Certificate Management** (or set `VC_HUB_URL` to a covered host name), then run the installer again. Unattended runs (`--yes`, `update`, non-interactive shells) skip the whole step unless the answer file sets `VC_HUB_TRUST_CERT=yes`. |
| Ports          | Detects occupied ports, shifts to the next free one and reports each substitution.               |
| Keycloak realm | Renders the realm template with the deployment origin and the VC Hub credentials, then imports it on the **first** Keycloak start. |
| Health         | Waits for both databases, Keycloak and the application (`--wait`). The observability services are probed separately and only produce warnings. |
| Verification   | Confirms the realm's OpenID configuration, that the `mems` client accepts the deployment redirect URI, and that the `vchub` identity provider is offered. |
| Data safety    | `update` compares the set of named volumes before and after and fails if it changed.             |
| Logging        | Writes one timestamped log per run and replaces every generated secret with `******`.            |

---

## 5. Finish the setup in VC Hub

Two steps cannot be automated because they change **VC Hub**, a separate system
MEMS has no administrative access to. The installer prints both, with the
hostname and ports that were actually used, at the end of every install and
update.

**1. Register the MEMS client.** In the VC Hub administration UI, create or
update the OpenID client you named during the installation:

```text
Redirect URI        https://<hostname>:<keycloak-https-port>/realms/mems/broker/vchub/endpoint
Logout redirect URI https://<hostname>:<keycloak-https-port>/realms/mems/broker/vchub/endpoint/logout_response
```

**2. Enable the Walm driver and allow embedding.** In the VC Hub
`appsettings.json`, then restart VC Hub:

```jsonc
{
  "Driver": { "EnabledDrivers": "...,Walm" },
  "CSP": { "frame-ancestors": "'self' https://<hostname>:<mems-app-https-port>" }
}
```

Recommended afterwards:

- Change the Keycloak and Grafana administrator passwords ([3.3](#33-the-initial-credentials)).
- Replace the self-signed certificate — either distribute it to the clients,
  or reinstall with `CERT_MODE=byo` and your own certificate. It expires after
  825 days.
- Copy any private CA certificate into `keycloak-truststore` (for Keycloak) or
  `mems-truststore` (for MEMS) and restart the stack.

---

## 6. Check the installation

**Linux**

```bash
sudo ./install-mems.sh status
```

**Windows**

```powershell
.\install-mems.ps1 status
```

`status` prints the installed version, the active release, the configuration path
and `docker compose ps`. Every core service must report `healthy`.

Then open `https://<hostname>:<mems-app-https-port>/` in a browser. You should be
redirected to Keycloak and see a VC Hub login option. A certificate warning is
expected with self-signed certificates.

### 6.1 Trust the VC Hub certificate later

If the VC Hub certificate was skipped during the installation, or VC Hub was
given a new certificate afterwards, fetch it again without reinstalling:

**Linux**

```bash
sudo ./install-mems.sh trust-vchub
```

**Windows (elevated PowerShell 7)**

```powershell
.\install-mems.ps1 trust-vchub
```

The command downloads the certificate over TLS, writes it as PEM to
`vchub-server.crt` in the configuration directory, reports its subject
alternative names and warns when they do not cover the VC Hub host name. It then
asks whether to copy it into the MEMS and Keycloak truststores. The URL comes
from `--vchub-url`, an `--answers` file or the installed environment file;
otherwise it is prompted for. Apply it afterwards with `install-mems compose-apply`.

---

## 7. Update

An update keeps the environment file, the certificates and every database volume.
It never prompts. There is **no automatic rollback**, so back up first.

### 7.1 Back up

**Linux**

```bash
sudo mkdir -p /var/backups/mems
sudo chmod 700 /var/backups/mems
sudo cp /etc/wago/mems/mems.env /var/backups/mems/mems.env
PGUSER=$(sudo sed -n 's/^POSTGRES_USER=//p' /etc/wago/mems/mems.env)
sudo docker exec postgres-mems-app pg_dumpall -U "$PGUSER" | sudo tee /var/backups/mems/mems-app.sql > /dev/null
sudo docker exec postgres-mems-keycloak pg_dumpall -U "$PGUSER" | sudo tee /var/backups/mems/keycloak.sql > /dev/null
```

**Windows**

```powershell
$backup = 'C:\Backup\MEMS'
New-Item -ItemType Directory -Path $backup -Force | Out-Null
$envFile = "$env:ProgramData\WAGO\MEMS\config\mems.env"
Copy-Item $envFile $backup
$pgUser = ((Select-String -Path $envFile -Pattern '^POSTGRES_USER=').Line -split '=', 2)[1]
docker exec postgres-mems-app pg_dumpall -U $pgUser | Set-Content "$backup\mems-app.sql"
docker exec postgres-mems-keycloak pg_dumpall -U $pgUser | Set-Content "$backup\keycloak.sql"
```

The dumps contain credentials — store them like the environment file.

### 7.2 Run it

**Linux**

```bash
sudo ./install-mems.sh update --bundle ./mems-offline-<newer-version>.tar.gz
```

**Windows**

```powershell
.\install-mems.ps1 update --bundle .\mems-offline-<newer-version>.tar.gz
```

Add `--dry-run` to print the plan without changing anything.

### 7.3 What it does

- Values already present in the environment file are kept; only keys that are new
  in the bundle's template are added.
- **Keys you added to the environment file by hand are not carried over** — the
  file is rebuilt from the new template. Re-apply your additions from the backup
  afterwards.
- A downgrade is refused with exit code `7`; `--force` overrides it.
- If the bundle declares `minUpgradeFrom` and the installed version is older, the
  update is refused with exit code `7`. Install the intermediate version first.
- The set of named volumes is compared before and after; a change fails the
  update with exit code `5`.
- The previous release directory is kept for one generation; older ones and their
  images are removed.

### 7.4 If the update fails

The stack may already be running the new images while `state.json` still names the
old version. Nothing is rolled back automatically. Reinstall the previous bundle
and, if the new version already migrated the schema, restore the dumps from 7.1:

**Linux**

```bash
sudo ./install-mems.sh update --bundle ./mems-offline-<previous-version>.tar.gz --force
```

**Windows**

```powershell
.\install-mems.ps1 update --bundle .\mems-offline-<previous-version>.tar.gz --force
```

Keep the failing run log for the support request — `/var/log/wago/mems/` on
Linux, `%ProgramData%\WAGO\MEMS\logs\` on Windows.

---

## 8. Uninstall

**Keep the data (default).** Stops and removes the containers and the bundled
images. Database volumes, certificates and the environment file remain, so a
later `install` reconnects to the existing data.

**Linux**

```bash
sudo ./install-mems.sh uninstall
```

**Windows**

```powershell
.\install-mems.ps1 uninstall
```

**Remove everything.**

> **Warning — irreversible.** `--purge-data` deletes every MEMS database volume,
> every generated certificate and the environment file. All measurement history,
> component configuration and Keycloak users in the MEMS realm are lost. Back up
> first ([7.1](#71-back-up)).

**Linux**

```bash
sudo ./install-mems.sh uninstall --purge-data
```

**Windows**

```powershell
.\install-mems.ps1 uninstall --purge-data
```

The installer asks for confirmation; use `--yes` only in automation.

After either variant:

- On Windows the installer logs live under the installation root and are removed
  with it. Copy them out first if you need them. On Linux they stay in
  `/var/log/wago/mems/`.
- The MEMS client registration in **VC Hub** is not touched and its secret stays
  valid. Remove it in VC Hub if the installation is gone for good.

---

## 9. Troubleshooting

Every run writes a log with generated secrets replaced by `******`:

- Linux: `/var/log/wago/mems/<command>-<timestamp>.log`
- Windows: `%ProgramData%\WAGO\MEMS\logs\<command>-<timestamp>.log`

The logs are never pruned automatically — clean the directory up periodically.

### Running `docker compose` by hand

A bare `docker compose` command cannot resolve this installation: it needs the
project name, the environment file, the project directory and both compose files.
The installer supplies them for you:

| Purpose                              | Command                          |
| ------------------------------------ | -------------------------------- |
| Validate the effective configuration | `install-mems compose-config`    |
| Apply the configuration (`up -d`)    | `install-mems compose-apply`     |

The same flags are also written to two ready-made wrappers, whose paths appear in
the installation summary. Copy the flags out of them for any other subcommand,
such as `logs` or `ps`:

| Purpose                              | Linux                                      | Windows                                              |
| ------------------------------------ | ------------------------------------------ | ---------------------------------------------------- |
| Validate the effective configuration | `/opt/wago/mems/scripts/compose-config.sh` | `%ProgramData%\WAGO\MEMS\scripts\compose-config.ps1` |
| Apply the configuration (`up -d`)    | `/opt/wago/mems/scripts/compose-apply.sh`  | `%ProgramData%\WAGO\MEMS\scripts\compose-apply.ps1`  |

### Exit codes

| Code | Meaning       | First things to check                                                                                     |
| ---- | ------------- | --------------------------------------------------------------------------------------------------------- |
| `0`  | Success       | —                                                                                                          |
| `1`  | Usage         | Unknown option or command, or a value missing in a non-interactive run. Run `help <command>`; in automation pass `--yes` **and** a complete answer file. |
| `2`  | Preflight     | Not root / not elevated, Docker not installed or not running, no Compose v2 plugin, wrong architecture, no free port, or MEMS is already installed (use `update`, or `--force`). |
| `3`  | Bundle        | Archive missing, truncated, not a MEMS bundle, or a checksum/signature mismatch. Copy it again and re-verify. A **signature** failure means the bundle is not what WAGO published — do not install it, report it. |
| `4`  | Images        | `docker load` failed (usually disk space — check `docker system df`), or a locally present image differs from the bundle. Remove it with `docker image rm <ref>` and re-run. |
| `5`  | Unhealthy     | The stack did not become healthy within 600 s, or the set of volumes changed during an update.              |
| `6`  | Provisioning  | The realm was not imported, the `mems` client rejected the redirect URI, or the certificate could not be generated. The run log contains the Keycloak container log. |
| `7`  | Version gate  | Downgrade refused (pass `--force` only if you accept that the databases may already have been migrated forward), or `minUpgradeFrom` not met — install the intermediate bundle first. |

### The stack does not become healthy

These commands are identical on both platforms:

```bash
docker compose --project-name mems ps
docker logs mems-app
docker logs mems-keycloak
docker logs postgres-mems-app
```

Common causes: a published port taken by a process that started after the
preflight; a database volume holding data from a different major version; or slow
storage — the first Keycloak start imports the realm and can take several
minutes. Warnings such as `observability: grafana did not answer` do **not** fail
the installation.

### Login does not complete

1. Confirm both [VC Hub steps](#5-finish-the-setup-in-vc-hub) were done with the
   exact URLs the installer printed.
2. Confirm the browser reaches the **Keycloak** HTTPS port, not only the MEMS
   port.
3. If VC Hub uses a private CA, place its certificate in `keycloak-truststore`
   (and in `mems-truststore` if MEMS must trust it directly) and restart the
   stack. `install-mems trust-vchub` does this for the VC Hub server
   certificate itself ([6.1](#61-trust-the-vc-hub-certificate-later)).

### The deployment hostname changed

Re-running `install --force --hostname <new>` is **not** enough: the existing
certificate is kept, and Keycloak does not re-import a realm that already exists.
Back up ([7.1](#71-back-up)), then `uninstall --purge-data` and install again
with the new hostname.

---

## 10. Configuration

The environment file is the single source of truth for a running installation.
Every key is documented with comments in `.env.example` inside the active release
directory. Edit only what you need, then apply:

**Linux**

```bash
sudo nano /etc/wago/mems/mems.env
sudo ./install-mems.sh compose-apply
```

**Windows (elevated PowerShell 7)**

```powershell
notepad "$env:ProgramData\WAGO\MEMS\config\mems.env"
.\install-mems.ps1 compose-apply
```

The file is root-only (Linux `0600`) / administrators-only (Windows). Keep it
that way. An `update` rebuilds it from the new bundle's template — see
[7.3](#73-what-it-does).

### Keys the installer sets

Everything else comes from the template unchanged.

| Key                           | Source    | Meaning                                             |
| ----------------------------- | --------- | --------------------------------------------------- |
| `DEPLOY_HOSTNAME`             | prompted  | Hostname or IP clients use for the MEMS application |
| `KEYCLOAK_URL`                | prompted  | Public Keycloak HTTPS origin; also controls its certificate hostname |
| `POSTGRES_PASSWORD`           | generated | Shared PostgreSQL password                          |
| `KEYCLOAK_ADMIN_PASSWORD`     | generated | Keycloak administrator password                     |
| `GRAFANA_ADMIN_PASSWORD`      | generated | Grafana administrator password                      |
| `OTEL_API_KEY`                | generated | Shared key between the application and the collector |
| `VC_HUB_URL`                  | prompted  | External VC Hub HTTPS origin                        |
| `VC_HUB_CLIENT_ID`            | prompted  | OpenID client MEMS uses at VC Hub                   |
| `VC_HUB_CLIENT_SECRET`        | prompted  | The corresponding secret — treat as a credential    |
| `*_PORT`                      | derived   | Shifted to the next free port when the default is taken |
| `KC_TRUSTSTORE_HOST_DIR`, `APP_TRUSTSTORE_HOST_DIR`, `NGINX_CERTS_HOST_DIR` | derived | Certificate and truststore directories on the host |

The VC Hub client keys are used by the installer to render the Keycloak realm. `VC_HUB_URL` is
also referenced by Compose for the application CSP; `KEYCLOAK_URL` configures Keycloak itself and
the MEMS backend.

`KC_LOG_LEVEL` defaults to `INFO`. `DEBUG` is very verbose and can expose request
detail — do not leave it on in production.

Grafana SMTP is disabled in the offline overlay because the bundle ships no mail
server.

---

## Support

Include with any support request:

- the output of `install-mems.sh status` (Linux) or `install-mems.ps1 status` (Windows),
- the installer log of the failing run (secrets are already scrubbed),
- `BUILD-INFO.json` from the active release,
- `docker compose --project-name mems ps`.

Do not send the environment file or a database dump — both contain credentials.
