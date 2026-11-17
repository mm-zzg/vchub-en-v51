# Windows Environment

VC Hub provides installation packages for the 64-bit Windows operating system.

Recommended Systems for Installation:

- Windows Server 2012 R2
- Windows Server 2016
- Windows Server 2019
- Windows Server 2022
- Windows 10  (Not supported in Home Edition)
- Windows 11  (Not supported in Home Edition)

## **Installation Steps**

1. Run the installation package program as an administrator.
2. Select the installation language.
   <br>![alt text](5.png)
3. Perform a port check, if the port is occupied, the installation cannot proceed. 
      ![alt text](6.png)
4. Read and accept the license agreement.
      ![alt text](7.png)
5. Choose the installation location; the default path is: "C:\Program Files\WAGO Visualization And Control Hub".
      ![alt text](8.png)
6. Select the VC Hub application data directory.
      ![alt text](9.png)
7. Prepare for installation.
      ![alt text](10.png)
8. The installation is complete.
      ![alt text](11.png)
9.  After completion, the default access to the VC Hub site is: `http://localhost:8066`. After the installation, you will enter the configuration wizard interface.

## **Configuration Steps**

1. Create an administrator user. Remember this username and password, as you will use them to log in for the first time. 
      ![alt text](12.png)
2. Port configuration, configure HTTP, HTTPS ports, and remember the access port. 
      ![alt text](13.png)
3. After completing the above steps, wait for the program to load, and then you can log in to the default-created workspace with the user created in step 1.

**Note**:

After each installation, a new empty workspace will be created by default. To return to the original workspace, you need to log in to the new workspace first and then manually open the original workspace from the workspace list.

## **Security Configuration (Optional)**

To further enhance system security, it is recommended to perform the following steps after configuration to set permissions on the **installation directory and application data directory**, allowing only specific users to access or modify them. This ensures that sensitive data is well protected and potential risks are minimized.

1. Create a dedicated service account<br>
      Create a dedicated account in Windows local users and groups (e.g., VCHubSvc):
      ![alt text](14.png)
2. Set service **installation directory** permissions<br>
      Navigate to the service installation directory (e.g., C:\Program Files\WAGO Visualization And Control Hub), right-click the mouse, select "Properties" → "Security"
       - Based on the actual security requirements, select the users or groups to be retained, and delete the unnecessary ones (such as Users, Everyone).
       - Add the VCHubSvc user and grant Read, Write, and Modify permissions.
       - Ensure the changes are applied to all subfolders and files.
       Note: This step must be completed before changing the service logon account; otherwise, the service may fail to start or restart.
3. Modify the service logon account<br>
      In Services (services.msc), locate the VC Hub service → right-click → Properties → Log On → select "This account":
       - Enter .\VCHubSvc and the password.
       - Save and restart the service.
4. Set application **data directory** permissions<br>
     Navigate to the application data directory chosen during installation (e.g., C:\ProgramData\WAGOVisualizationAndControlHub), in the right-click menu, click "Properties"→ "Security":
       - Based on the actual security requirements, select the users or groups to be retained, and delete the unnecessary ones (such as Users, Everyone).
       - Add the VCHubSvc user and grant Read, Write, and Modify permissions.
       - Ensure the changes are applied to all subfolders and files.
5. Verify configuration<br>
      Access the VC Hub site (e.g., `http://localhost:8066`) and confirm that the site is running normally.

## **Uninstallation Steps**

1. Enter the software uninstall list from the Control Panel. Find VC Hub and proceed with the uninstallation.
      ![alt text](15.png)
2. Confirm the uninstallation to complete the removal of the application.
      ![alt text](16.png)






