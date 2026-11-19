# Integration into VC Hub

WAGO EMS is designed to operate as an integrated part of the VC Hub platform rather than as a standalone application. In this architecture, VC Hub provides the identity layer, user access control, runtime visualization, data integration, and communication services, while WAGO EMS focuses on microgrid supervision, optimization, control logic, and energy management.

This integration model allows WAGO EMS to use the strengths of VC Hub for both operator experience and system connectivity, while keeping the microgrid control logic centralized and consistent.

## Authentication and authorization

User access to WAGO EMS is based on VC Hub as the identity provider (IdP). The user-facing application uses the Authorization Code Flow to log in through VC Hub. In this flow:

- the user signs in to VC Hub
- the application receives an authorization code
- the code is exchanged for access and refresh tokens
- the tokens are used to access the authorized WAGO EMS functions

This approach ensures that authentication and authorization are managed centrally. User roles, permissions, and access policies remain consistent with the broader VC Hub system, which is especially important in industrial environments where operator rights and responsibilities need to be clearly controlled.

By using VC Hub as the IdP, WAGO EMS benefits from a single sign-on style experience and a unified security model across the platform.

## Service-to-service integration with Client Credentials Flow

WAGO EMS backend services use Client Credentials Flow to connect to VC Hub for machine-to-machine communication. This is used for non-user service access, where the backend needs to act on behalf of an application rather than a specific user.

With this model, the WAGO EMS backend authenticates against VC Hub using its configured client credentials and receives a service access token. This token is then used to:

- subscribe to data from VC Hub
- read device status, measurements, and tags
- trigger control actions and setpoints
- obtain alarm and event information
- access runtime and configuration interfaces exposed by VC Hub

This pattern is suitable for backend automation because it provides secure, delegated access without requiring a human user session. In other words, the WAGO EMS service can continuously communicate with VC Hub in order to monitor the microgrid and issue control commands according to its operating logic.

## Device synchronization and communication model

In WAGO EMS, the microgrid devices and logical assets are defined and managed as part of the WAGO EMS model. These definitions are synchronized to VC Hub so that the system maintains a consistent view of the deployed assets across the platform.

Once synchronized, VC Hub acts as the communication and integration layer to the actual field devices. In practice:

- WAGO EMS defines the logical device model, operating logic, and microgrid structure
- VC Hub handles the system-level integration, data acquisition, and communication with the actual devices
- the device data and control points are exposed through the VC Hub runtime and APIs
- WAGO EMS can then use this information to perform dispatch, optimization, and supervisory control

This separation is important. WAGO EMS remains responsible for the energy management strategy, while VC Hub remains responsible for the runtime connection to equipment, industrial protocols, and operational data integration.

## Embedded VC Hub runtime views

WAGO EMS also embeds selected VC Hub runtime pages and UI components. This allows the microgrid application to reuse the flexible configuration capabilities of VC Hub for process visualization, dynamic dashboards, and operator interaction.

By embedding VCHub runtime screens, WAGO EMS can combine:

- microgrid energy management logic
- reuse of proven VC Hub visualization components
- flexible page configuration for dashboards and process views
- consistent operator experience across monitoring and control tasks

This is especially valuable for displays such as:

- energy flow overview
- battery and storage status
- generation and load overview
- alarm and event displays
- system overview pages for operators and maintenance staff

The embedded approach reduces duplicated engineering effort and makes it easier to use VC Hub's configuration flexibility while still maintaining WAGO EMS as the supervisory control layer.

## Benefits of the integrated architecture

The integration of WAGO EMS into VC Hub creates a clear and scalable architecture for microgrid operation:

- centralized identity and role-based access through VC Hub
- secure service integration using OAuth Client Credentials Flow
- synchronized device models between WAGO EMS and VC Hub
- direct communication from VC Hub to the real field devices
- flexible runtime pages and visualization for operators
- a unified platform for monitoring, control, and energy optimization

In summary, WAGO EMS uses VC Hub not only as a visualization layer but also as a trusted identity provider, secure service integration platform, and communication backbone for the microgrid environment. This creates a strong foundation for safe, scalable, and efficient microgrid operation.