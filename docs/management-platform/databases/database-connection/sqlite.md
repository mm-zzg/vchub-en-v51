# SQLite

On this page, we will demonstrate how to connect VC Hub to SQLite.

1. On the "**Databases**" -> "**Database Connection**" page, click the "Add" button. 
    ![alt text](6.png)
2. In the following pop-up window, select SQLite and click the Next button.
    ![alt text](16.png)
3. Enter the following information in the configuration interface (Note: The following data is only an example, please fill in according to the actual situation).

    Since SQLite is an open source embedded relational database that implements a self-contained, serverless, configuration-less, transactional SQL database engine. It is a zero-configuration database.

    So creating a SQLite database connection means creating a SQLite file locally. So there is no need for Host, Port, Username, Password, etc. You just need to check where the SQLite file is stored.

    ![alt text](17.png)

     - Name: Demo
     - Storage Path: {WorkspaceDirectoy}/database/history 
     - Database name: history
     - Connection timeout(ms): 10000
     - Maximum Query Points：1000000
     - Query Timeout(s)：30

    **Notes:** 

    1. The database name is the name of the SQLite file without suffix. 

    2. The storage path of SQLite file supports placeholders such as"{WorkspaceDirectory}/database/history". This allows users to create a history database file within workspace folder by utilizing the placeholder in the storage path. 

4. Click **"OK"** button, the popup window will be closed and the list of database connections will be displayed. The connection status of the data in the list is "Connected".
    ![alt text](18.png)

