# SQL Server

On this page, we will demonstrate how to connect VC Hub to SQL Server. 

1. On the "**Databases**" -> "**Database Connection**" page, click the "Add" button. 
    ![alt text](6.png)
2. In the following window, select SQL Server and click the "Next" button. 
    ![alt text](10.png)
3. Get the SQL Server connection string information, such as the following two formats:

    User ID=sa;Password=admin@12345;Server=localhost,1433;Database=scada-history;encrypt=true;TrustServerCertificate=true;; jdbc:sqlserver

    jdbc:sqlserver://localhost:1433;database=scada-history;user=sa;password=admin@12345;encrypt=true;TrustServerCertificate=true;

    Enter the following information in the configuration interface (Note: the following data is only an example, please fill in according to the actual situation).

    ![alt text](11.png)

     - Name: Demo
     - Host: localhost
     - Port: 1433
     - Database Name: scada-history
     - UserName: sa
     - Password: admin@12345 
     - Extension Properties: encrypt=true;TrustServerCertificate=true;
     - Connection Timeout (ms): 10000
     - Maximum Query Points: 5000000
     - Query Timeout(s): 30

4. Click the **"OK"** button, the pop-up window closes and the list of database connections is displayed. The connection status of the data in the list is "Connected".
    ![alt text](12.png)





