# Alarm History Storage

VC Hub allows you to store alarm data in a database. Basic data about the alarms that have occurred, such as path, time, level, status, etc. can be stored.

Multiple history database can be created, where you can store a part of the alarms in one database and another part of the alarms in another database. And set different storage policies for each library.

On the Historical Alarm control, you can select a history bank for data filtering.

## **Create a history database**

1. Click "**Alarming**"->"**Alarm History Storage**" to enter the list of history storage.
    ![alt text](6.png)
2. Click "Add" button. Set the properties in the Add popup window. 
    ![alt text](7.png)
    The following is displayed when “Database” is selected as the type:
    ![alt text](8.png)

**Properties of the Popup**

| **Name**            | **Description**      |
|---------------------|---------------------|
| Name                | The name of the alarm history storage.  |
| Type                | Drop down selections containing: Database and Remote.   When Database is selected for Type, in the Database Connection field, select a locally created database. When Remote is selected, you need to select the remote node as well as the remote alarm history storage.   |
| Database Connection | Drop-down list to select the database that has been created in the "Databases" -> "Database Connection" page. Single-select only.  <br> **Note:** The dropdown options do not include databases of type InfluxDB.  |
| Description         | Description of the alarm history storage.   |
| Retention Days      | The number of days that the alarm data under this alarm history storage will be retained in the database. |
| Min Priority        | Sets which levels of alarm data are stored. Only alarms with a priority level equal to or higher than the specified priority level are stored.|

The following is displayed when “Remote” is selected as the type:
    ![alt text](9.png)

**Properties of the Popup**

| **Name**             | **Description**    |
|----------------------|--------------------|
| Name                 | The name of the alarm history storage.  |
| Type                 | Drop down selections containing: Database and Remote.   When Database is selected for Type, in the Database Connection field, select a locally created database. When Remote is selected, you need to select the remote node as well as the remote alarm history storage.  |
| Remote Node          | Drop down to select a node name that forms a networking with the current node.    |
| Remote Alarm Storage | Depending on the remote node selected, the alarm history storage created under that node is displayed.   |
| Query Only           | Default is turned off. When it is turned on, only remote alarms can be queried, and new alarms generated at the remote node will not be stored in the database; if it is turned off, new alarms generated at the remote node will be stored in the database. The database mentioned here refers to the database used by the remote alarm history storage. |
| Description          | Description of the alarm history storage.  | 

3.When the settings are complete, click the OK button.

## **History Database Application**

Select the history storage in the filter criteria of the Historical Alarm control, and the next step will be to filter the data in the selected history storage.

![alt text](10.png)

 

