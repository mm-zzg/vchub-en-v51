# Requirements

MEMS is installed as a Docker Compose stack. Before you start, make sure the
target host and the connected VC Hub deployment satisfy the following
conditions.

## MEMS host requirements

| Requirement    | Minimum                                                           | Checked by the installer |
| -------------- | ----------------------------------------------------------------- | ------------------------ |
| Docker Engine  | 24.0 or newer, running and usable by the installing account       | that it runs             |
| Docker Compose | v2 plugin (`docker compose version` must succeed)                 | yes                      |
| Architecture   | x86-64 (`linux/amd64` images)                                     | yes                      |
| Privileges     | root (Linux) or an elevated PowerShell 7 session (Windows)        | yes                      |
| Disk space     | ~20 GiB free                                                      | warning only             |
| Memory         | 8 GiB recommended                                                 | no                       |
| Linux          | GNU coreutils and GNU `tar` (default on mainstream distributions) | no                       |
| Windows        | Windows 10 1803 / Windows Server 2019 or newer, PowerShell 7+     | no                       |

Nothing else is required on the MEMS host: no internet, no proxy, no registry
login, no Java/JDK, no OpenSSL, and no `jq`, `curl`, `python`, `git` or `cosign`.
`openssl` is run inside a bundled image. PostgreSQL, Keycloak and nginx come with
the bundle.

> **SELinux.** The bundled compose files do not label their bind mounts (`:z` /
> `:Z`). With SELinux in enforcing mode the containers cannot read
> `/etc/wago/mems`. Set the host to permissive, or add the labels yourself,
> before installing.

### Ports

Open the firewall for at least `MEMS_APP_HTTPS_PORT` (`9443`) and the endpoint
configured by `KEYCLOAK_URL` — browsers are redirected to Keycloak directly.
If a default port is already in use, the installer moves to the next free one and
reports the substitution; the value it settled on is in the environment file.

All HTTPS ports are published by the bundled nginx reverse proxy, which
terminates TLS and forwards to the services over the internal Docker network.
Keycloak, MEMS and Grafana publish no ports of their own.

| Key                   | Default | Service                             |
| --------------------- | ------- | ----------------------------------- |
| `MEMS_APP_HTTPS_PORT` | `9443`  | MEMS — the main entry point         |
| `KEYCLOAK_HTTPS_PORT` | `8443`  | Keycloak                            |
| `GRAFANA_HTTPS_PORT`  | `3443`  | Grafana                             |
| `KEYCLOAK_DB_PORT`    | `5433`  | Keycloak PostgreSQL                 |
| `MEMS_DB_PORT`        | `5434`  | MEMS PostgreSQL                     |

The observability stack (Loki, Tempo, Prometheus, the OpenTelemetry Collector
and blackbox-exporter) publishes no host ports at all. Those services are
reachable on the internal Docker network only and are inspected through Grafana.

## VC Hub requirements

MEMS also depends on a working VC Hub deployment. Make sure the VC Hub host and
browser endpoints meet the requirements documented in [System Requirements](../overview/system-requirements.md).
