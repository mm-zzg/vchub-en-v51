# MQTT Broker

The MQTT Broker is a core component of the MQTT protocol, responsible for forwarding messages between publishers and subscribers.

You can configure its parameters by clicking **“Node” -> “MQTT Broker”**.

![alt text](17.png)

**Parameters:**

| **Name**                     | **Description**  |
|------------------------------|--------------------------------|
| Enable TCP                   | Enable the tcp port.|
| TCP Port                     | Specifies the port used for non-secure MQTT connections. Default is 1883.|
| Enable TLS                   | Enable this option to use secure communication over TLS.  Before enabling, you must configure the MQTT Broker certificate. If the certificate is not configured, the interface will prompt “Please configure the MQTT Broker certificate first” and disable the option from being enabled. |
| TLS Port                     | Specifies the port used for secure MQTT connections. Default is 8883. |
| Auto Reconnect Delay Time(s) | The delay time (in seconds) before the client automatically attempts to reconnect after a disconnection. Default is 30.|
| Keep Alive Period Time(s)    | The interval (in seconds) at which heartbeat (keep-alive) packets are sent to maintain the connection. Default is 60.|
| Enable|Enable the rate limiting. Default diasbled.Rate Limiting is used to impose upper limits on the message rate and data volume for each client.|
| Statistics period(min)|Unit is minutes. The statistical period of rate limiting.|
| Maximum Messages|The maximum number of sent messages by the client within a statistical period.|
| Maximum Data Size(MB)|The maximum size of sent messages by the client within a statistical period.|


## Precautions Before Enabling TLS

Before enabling TLS, you must first go to the [Certificate Management](../certificate-management/index.md) page to configure the TLS certificate used by the MQTT Broker.

You can choose to upload an existing TLS certificate or use a self-signed certificate provided by the system. Once configured, return to this page to enable the TLS feature.

