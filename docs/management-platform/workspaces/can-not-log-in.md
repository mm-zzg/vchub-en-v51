# Cannot Log In

**Note:** If you forget all user passwords for the current workspace you will not have any opportunity to log into the current workspace. Please make sure to securely store the password.

If you are unable to log into the current workspace, you can try switching workspaces or creating a new workspace.

# Method 1: Switching Workspaces

If you have other workspaces in your system and have the login information for those workspaces, you can manually switch to one of them.

1. **Log in to the VC Hub installation server.**
1. **Go to the user data directory.**
      - For Windows installation, the default user data directory is: “%ProgramData%\WAGOVisualizationAndControlHub”, usually located at “C:\ProgramData\WAGOVisualizationAndControlHub”.
      - For Linux installation, the default user data directory is: `/usr/share/`wagovisualizationandcontrolhub.
      - If you changed the user data directory during installation, go to the directory you modified.
1. **Navigate to the \Workspaces folder.**
      - This directory contains all the workspaces, with each workspace stored in its own separate folder.Use the workspace Id as the folder name.
      ![alt text](23.png)
      - Open each workspace folder and check the worspace name in the **.ini** file. Find the workspace where you know the username and password, and record its Id.
      ![alt text](21.png)
4. **Modify the ".ini" file in the root directory of the workspace folder.**<br> Change the **Current** field to the Id recorded in the previous step.
      ![alt text](22.png)
5. **Restart the service.**
6. **Log in with the switched workspace user.**

# **Method 2: Create a New Workspace**

If there are no other available workspaces in your system, Method 1 will not be applicable. In this case, you can choose to create a new workspace.

1. **Log in to the VC Hub installation server.**
2. **Navigate to the program installation directory.**
      - Default installation directory for Windows: `C:\Program Files\WAGO Visualization And Control Hub`
      - Default installation directory for Linux: `/usr/local/bin/wagovisualizationandcontrolhub-x.x.x-linux-x64`
      - If you changed the installation directory during installation, please navigate to your actual installation directory.
3. **In the current version directory, navigate to the *MarkFiles* folder and delete the `workspace_initialized` file.**
      ![alt text](image.png)
4. **Restart the service.**
5. **Refresh the login page, and you will be guided to create a new workspace.Simply enter a username and password to complete the workspace creation.**
