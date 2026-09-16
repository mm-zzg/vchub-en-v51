# VC Hub Service Account and File Permissions

## Overview

The VC Hub installer requires administrator or root privileges to copy application files, configure file permissions, and register the system service. These privileges are required only for installation, repair, and uninstallation.

After installation, the VC Hub service runs under a dedicated non-privileged identity. The administrator or root account used to install VC Hub is not used as the runtime identity.

Running VC Hub with a dedicated identity limits the impact of application errors or security vulnerabilities and separates VC Hub from other services on the host.

## Service Accounts

The installer configures the service identity automatically. Do not create another service account or change the configured identity unless instructed by WAGO support.

| Platform | Service identity | Account type |
|---|---|---|
| Windows | `NT SERVICE\WAGO_Visualization_And_Control_Hub` | Windows virtual service account |
| Linux | `vchub` | Non-login system account |

### Windows

The Windows virtual service account:

- Is managed by Windows and does not require a password.
- Is not a regular local or domain user.
- Is not a member of the local Administrators group.
- Exists as the identity of the registered VC Hub service.

Do not change the service to run as `LocalSystem`, an administrator, or a regular user account.

### Linux

The installer creates the `vchub` system account if a compatible account does not already exist. The account has no interactive login shell and is not granted `sudo` access.

The installer does not remove the `vchub` account during uninstallation. Keeping the account preserves a stable service identity for a later reinstallation.

Do not assign a password to `vchub`, add it to the `sudo` group, or add it to the `sudoers` file.

## File System Permissions

The installer configures the required permissions for the selected application and data directories.

| Location | Service access |
|---|---|
| Application files | Read and execute |
| Application directory in general | No general write access |
| Required runtime files and subdirectories | Write access only where required |
| VC Hub data directory | Read and write |
| Unrelated system locations | No access is granted by the installer |

The exact runtime-writable files and subdirectories are managed by the installer and may change between releases. Do not grant the service identity write access to the complete application directory unless instructed by WAGO support.

When a custom application or data directory is selected, the installer applies the same permission model to that directory. On Linux, the service must also be able to traverse each parent directory. The installer checks this requirement and, when necessary, asks before changing parent-directory traversal permissions.

!!! warning

    Do not use broad permissions such as `chmod 777`, and do not make the VC Hub service an administrator or root service to resolve an access error. Review the affected path and grant access only to the required VC Hub runtime location.

## Verify the Runtime Identity

### Windows

Run the following command from PowerShell:

```powershell
Get-CimInstance Win32_Service `
  -Filter "Name='WAGO_Visualization_And_Control_Hub'" |
  Select-Object Name, StartName, State, PathName
```

Verify that `StartName` is:

```text
NT SERVICE\WAGO_Visualization_And_Control_Hub
```

You can also open **Services** (`services.msc`), open the properties of **WAGO Visualization And Control Hub**, and check the **Log On** tab.

### Linux

Run:

```bash
systemctl show wagovisualizationandcontrolhub.service \
  --property=User \
  --property=Group \
  --property=MainPID
```

Verify that the output contains:

```text
User=vchub
Group=vchub
```

To verify the identity of the running process, run:

```bash
pid="$(systemctl show \
  --property=MainPID \
  --value wagovisualizationandcontrolhub.service)"
ps -o user,group,pid,cmd -p "$pid"
```

## Using Ports Below 1024 on Linux

Linux normally restricts TCP and UDP ports below 1024 to privileged processes. WAGO recommends configuring VC Hub, its web server, and its drivers to use ports from 1024 through 65535 whenever possible.

For HTTP and HTTPS ports 80 and 443, consider using a reverse proxy that listens on the low port and forwards traffic to the default VC Hub ports. This keeps the VC Hub service without additional capabilities.

If VC Hub or a driver must bind directly to a port below 1024, grant only the `CAP_NET_BIND_SERVICE` capability to the VC Hub systemd service. Do not run VC Hub as root and do not add `vchub` to the `sudo` group.

### Enable Low-Port Binding

Run the following commands as a user with `sudo` privileges:

```bash
sudo install -d -m 0755 \
  /etc/systemd/system/wagovisualizationandcontrolhub.service.d

sudo tee \
  /etc/systemd/system/wagovisualizationandcontrolhub.service.d/10-privileged-ports.conf \
  > /dev/null <<'EOF'
[Service]
CapabilityBoundingSet=CAP_NET_BIND_SERVICE
AmbientCapabilities=CAP_NET_BIND_SERVICE
EOF

sudo systemctl daemon-reload
sudo systemctl restart wagovisualizationandcontrolhub.service
```

The service continues to run as `vchub`. The capability permits the service and its normally started child processes to bind to privileged ports; it does not grant general root access.

!!! note

    `CAP_NET_BIND_SERVICE` permits binding to any port below 1024. It cannot be restricted to one specific port. Enable it only when a low port is required.

### Verify Low-Port Binding

Check the service identity and capabilities:

```bash
systemctl show wagovisualizationandcontrolhub.service \
  --property=User \
  --property=Group \
  --property=AmbientCapabilities \
  --property=CapabilityBoundingSet
```

Then confirm that the configured port is listening:

```bash
sudo ss -lntup
```

If a driver is operated by a separate systemd service instead of by VC Hub, configure that service separately.

### Disable Low-Port Binding

Before removing the capability, configure all VC Hub ports to use port 1024 or higher. Then run:

```bash
sudo rm \
  /etc/systemd/system/wagovisualizationandcontrolhub.service.d/10-privileged-ports.conf

sudo systemctl daemon-reload
sudo systemctl restart wagovisualizationandcontrolhub.service
```

## Operational Considerations

- Installation, repair, and uninstallation still require administrator or root privileges.
- Do not manually change the service identity or recursively replace permissions on the application or data directory.
- After restoring files from a backup or copying them from another host, verify that the VC Hub service can still access the data directory.
- Third-party components may maintain data in their own locations. Permissions for those locations are managed by the corresponding component or installer.

## Troubleshooting Permission Errors

Permission-related problems may appear as **Access denied**, **Permission denied**, or **Read-only file system** messages.

1. Confirm that the service is running under the expected identity.
2. Identify the exact file or directory in the VC Hub or system log.
3. Confirm that the path is an intended runtime data location.
4. Check whether files were manually moved, restored, or copied after installation.
5. Reinstall VC Hub or contact WAGO support if the required permission is unclear.

On Linux, view recent service messages with:

```bash
sudo journalctl -u wagovisualizationandcontrolhub.service -n 100 --no-pager
```

Do not resolve an unknown permission error by granting root access or unrestricted write permissions.
