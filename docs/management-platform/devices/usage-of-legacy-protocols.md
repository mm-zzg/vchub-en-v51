# Usage of Legacy Protocols

Protocols like **Modbus TCP/RTU**, **SIEMENS S7**, are commonly used in industrial settings for communication with PLCs, I/O devices, and various automation equipment. However, they lack inherent support for **authentication and encryption**, posing security challenges in modern networks.

1. **Modbus TCP/RTU**: One of the oldest and most widely used protocols in industrial automation, Modbus is simple and reliable but lacks authentication and encryption mechanisms in its original form. This makes it vulnerable to attacks such as replay, unauthorized access, and data tampering. **Modbus TLS extension protocol is currently not supported.**
2. **SIEMENS S7**: The S7 protocol is specific to Siemens PLCs and also lacks built-in security features. The absence of authentication and encryption leaves it susceptible to network attacks, including interception and unauthorized commands, especially concerning for critical control applications.

Given these limitations, it’s increasingly essential to implement security measures such as **VPNs**, **segmented networks**, and firewalls to control access, as well as consider protocol gateways or proxies with security features to encapsulate these protocols securely when possible.
