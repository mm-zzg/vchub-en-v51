# IEC104 TLS

This page describes how TLS works for IEC104 devices in VC Hub, including TLS configuration, default port behavior, trust-store warning handling, and the actual **Yes/No** behavior in the certificate trust dialog.

## Enable TLS for an IEC104 Device

1. Open **Devices** -> **IEC104** and click **Add** (or **Edit** an existing device).
2. Check **Enable TLS**.
3. Configure server endpoints and ports.
4. Save and enable the device.

![alt text](14.png)

## Port Behavior with TLS

When **Enable TLS** is checked, VC Hub uses TLS-oriented default behavior:

- The TLS default server port is **19998**.
- For empty server rows, port defaults are switched automatically:
  - TLS enabled: default port is **19998**.
  - TLS disabled: default port is **2404**.

## Test Connection with TLS

- The **Test Connection** action uses the current form values.
- If **Enable TLS** is checked, the request includes the TLS flag.
- If TLS is not checked, the request is sent as non-TLS.

![alt text](15.png)

## Trust-Store Warning and Certificate Prompt

After a TLS-enabled device is started and connected, VC Hub checks whether the active endpoint certificate is trusted:

- If certificate is **not trusted**, a warning indicator appears.
- If certificate is **expired**, a warning indicator also appears.
- Clicking the warning opens the trust-store confirmation dialog.

![alt text](16.png)

## Dialog Behavior: Yes / No

### Yes

- If certificate state is **not trusted**:
  - VC Hub adds the endpoint certificate to trust store.
  - Trust-store cache is cleared.
  - TLS trust status is re-checked for visible devices.
- If certificate state is **expired**:
  - VC Hub does **not** add the certificate.
  - An error message is shown.

### No

- The dialog is closed.
- If the device is currently running, VC Hub disables (stops) that device.

![alt text](17.png)
![alt text](18.png)

## Notes

1. Trust-store checks are applied for TLS-enabled, started, and connected devices.
2. Endpoint status in **View** can show **Active** (currently connected endpoint) and **Standby** (configured but not currently used endpoint).
3. For stable TLS operation, ensure endpoint certificates are valid (not expired) and trusted before long-running communication.
