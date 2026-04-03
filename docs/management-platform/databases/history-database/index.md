# History Database

 The History Database module offers great functionality and flexibility for storing and accessing historical data. When tag history is enabled on VC Hub, data is automatically stored in the database in a valid format. This data can be used for querying charts and reports. Options for partitioning and deleting old data help to ensure that the system remains maintained with minimal additional work.

#### **Supported History Database Types**

1. **History Database:** Configuration for partitioning, preprocessing, and data cleanup of data stored into the database.
2. **Duplicated History Database:** Data is stored into both Database Connection 1 and Database  Connection 2 configurations for disaster recovery of historical data storageand queries. When database connection 1 fails, it will be switched to database connection 2 to continue to provide storage and query functions.
3. **Remote History Database:** Forwarding configuration for history database  and dual history database of other nodes in the group network, when using this configuration, data storage and query will use the history database configuration of the remote node.

