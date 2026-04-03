# Workspaces

 The **VC Hub** system can be divided into three main sections: **certificates** , **workspace** and **network** . Certificates are mainly used to activate the system and to secure overall access to the VC Hub system, while the network is mainly used tomanage the system's basic network information, redundancy, networking, and the configuration of complex network architectures.

 Except for the certificate and network-related modules, all other modules can be considered a subset of the workspace, which VC Hub can, so that a single workspace can be considered as an independent configuration container, where configuration items include:

- [Projects](../projects/index.md): The project manages the configuration pages. A project can have multiple page s, including 2D and 3D configurations, so that the user can draw the target industrial scenario in the project module according to the requirements.
- [Devices](../devices/index.md): VC Hub systems can be interfaced with a wide range of industrial protocols. The device module is used to manage the industrial protocol connection information to ensure that the system interacts with the actual industrial production equipment.
- [Assets and Tags](../assets-and-tags/index.md): The medium used by the system to display and process industrial data. Tags can be bound to the protocol information in the device module and configured in a specific way, and after successful configuration, the tags will receive data from the actual device and issue commands to the device via the corresponding protocol.
- [Alarming](../alarming/index.md): Mainly to configure the alarm history storage related information and stale alarm processing.
- [Scripts](../scripts/index.md): In relatively complex data processing scenarios, the user can edit JavaScript code through the script module to read and write values to some of the system data.
- [Databases](../databases/index.md): Used to configure the connection information between the system and external databases, through which connection tags, alarm history data can be recorded into the databases supported by VC Hub, such as Influx DB, MySQL, etc.
- [Security](../security/index.md): Configuration of roles and user information for individual workspaces, which is mainly used to manage the use of the system's functional privileges. The configuration of permissions only takes effect in the current workspace. In a multi-workspace scenario, each workspace will have a separate permission system.

## **Initial workspace**

 The startup of a VC Hub system is based on a workspace, which is an important basis for the operation of the system. The existence of a complete workspace folder in the server system is a prerequisite for the normal operation of the system.

 Therefore, when running the VC Hub system for the first time, the system will check whether any workspace files exist on the server system, and if they do not, then the system will initialize a workspace named Default in the data directory of the server system as the working directory of the system. In subsequent system operations, the data of the above mentioned modules will be stored in this initialized workspace folder.

## **Workspace Data Storage**

#### **Storage directory**

 All workspace data will be stored in the form of files in the data directory location on theserver system. Currently, the VC Hub system deployment server only supports Windows and Linux, and the storage location of the workspace directory differs between the two:

-  Windows: Usually points to C:\ProgramData\WAGOVisualizationAndControlHub \Workspaces\, which is a specific system directory for storing application data on Windows systems.
-  Linux: Fixed to /usr/share/WAGOVisualizationAndControlHub/ Workspaces.

#### **Directory structure**

 A complete root directory for workspace data should contain at least one .ini file and a workspace folder named with a random GUID. The following figure shows the workspace data directory in Windows.

![alt text](1.png)


- [Current Workspace Configure File](current-workspace-configure-file.md): The current workspace configuration file is a .ini suffix configuration file containing configuration information that serves as the basis for the startup of the VC Hub service.
- [Workspace Directory](workspace-directory.md): A single workspace directory stores all the workspace data of a workspace and contains the basic information of the workspace, named with a random GUID string, which also serves as aunique identifier of a workspace. A VC Hub node can contain several workspaces, and the workspace names must be different from one workspace to another.


