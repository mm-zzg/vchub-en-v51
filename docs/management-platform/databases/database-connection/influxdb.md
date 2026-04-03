# InfluxDB

InfluxDB is a high-performance time-series database that focuses on large amounts of time-series data and supports flexible customizable retention policies and SQL-like interfaces.

VC Hub supports **InfluxDB Enterprise** and **InfluxDB OSS V1**, but not **InfluxDB OSS V2**.

On this page, we will demonstrate how to connect VC Hub to InfluxDB.

1. On the "**Databases**" -> "**Database Connection**" page, click the "Add" button. 
   ![alt text](6.png)
2. In the following window, select InfluxDB and click the Next button. 
   ![alt text](19.png)
3. Get the information about the InfluxDB server, such as host, port, use SSL, user name, password, etc. Fill in the information into the configuration box and save it. (Note: The following data is only an example, please fill in according to the actual situation). 
   ![alt text](20.png)

    - Name: InfluxDB
    - Host: localhost
    - Port: 8087
    - Use SSL: Enabled
          - Data is transmitted over an encrypted channel between the VC Hub and the InfluxDB server, ensuring confidentiality and integrity. This prevents third parties from eavesdropping or tampering with the data, which is crucial when handling sensitive information.
    - Database Name: history
    - UserName: admin
    - Password: admin@12345 
    - Connection Timeout (ms): 10000

4. Click the **"OK"** button, the pop-up window closes and the database connection list is displayed. The connection status of the data in the list is "Connected".
   ![alt text](21.png)

