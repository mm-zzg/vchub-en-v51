# Security

MEMS uses Keycloak as its identity provider (IdP). Keycloak is configured to use VC Hub as an upstream IdP, so VC Hub authenticates the user while Keycloak brokers the identity to MEMS.

The sign-in flow is:

```text
MEMS --> Keycloak --> VC Hub
MEMS <-- Keycloak <-- VC Hub
```

MEMS does not connect directly to VC Hub for interactive user authentication.

## Security model

Each component has a distinct responsibility in the authentication flow:

- **MEMS** relies on Keycloak to authenticate users and establish application sessions.
- **Keycloak** acts as the IdP for MEMS and as an identity broker for VC Hub.
- **VC Hub** is the upstream IdP that authenticates the user.

When a user opens MEMS, the browser is redirected to Keycloak. Keycloak then redirects the user to VC Hub for authentication. After a successful sign-in, VC Hub returns the authentication result to Keycloak, and Keycloak completes the MEMS login.

MEMS does not maintain a separate user directory or an independent permission model for normal operation.

## User management

Manage upstream user accounts and their access in VC Hub. Do not create or manage daily user accounts in MEMS.

For information about managing users, roles, permissions, and access controls in VC Hub, see [Security](../management-platform/security/).

Keycloak administrators should maintain the VC Hub IdP configuration used by the MEMS realm. This configuration includes the VC Hub issuer URL, client ID, client secret, and redirect URIs created during MEMS installation.

For the required VC Hub client and redirect URI configuration, see [Installation and upgrade](installation-and-upgrade.md#5-finish-the-setup-in-vc-hub).

## Access control reminder

At present, MEMS does not have a separate role or permission model of its own. Users who successfully authenticate through the Keycloak and VC Hub sign-in flow have the same permissions in MEMS.

If VC Hub does not authenticate a user, Keycloak cannot complete the MEMS login and the user cannot access MEMS.

## Recommended practice

- Manage upstream user accounts and access policies in VC Hub.
- Keep the VC Hub IdP configuration in Keycloak aligned with the OpenID client registered in VC Hub.
- Restrict access to the Keycloak administration console and protect the VC Hub client secret.
- Regularly test the complete MEMS → Keycloak → VC Hub sign-in flow.