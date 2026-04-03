# Version Update Notes

 VC Hub is constantly evolving and being updated, with each new version bringing new features and bug fixes. Here, you can quickly preview the new features and resolved issues of the corresponding versions.

## Determining Your Current Version

 You can find out the version number of VC Hub you are currently using in the following two ways:

1.  In the bottom right corner of the management platform, you can find the corresponding VC Hub version number.
    ![alt text](5.png)
2.  In the top right corner of the configuration editing interface, you can click on this icon to get the corresponding VC Hub version number information.
    ![alt text](6.png)


## New Features

#### 5.0.X

- **License Management**: Support license activation, deactivation, refresh, update and deletion.
- **Force logout online user**: If the number of concurrent users reaches the license limit, the system will automatically force the earliest logged-in user to log out when a user with security permission logs in. Ensure that users with security permission can always access the system, or release the login slots for other users to use.

#### 4.5.X

- **License Management**: Activate the license using DRM. This version only supports the trial mode of the license.

#### 4.4.X

- **Logo and Name Modification**: The product logo has been replaced, and the product name has been changed from WAGO SCADA to WAGO Visualization and Control Hub, abbreviated as VC Hub.

#### 4.3.X

- **SVG Editor**: Through the SVG editor, users can modify and save attributes of SVG images in the library, such as color, size, text content, and visibility.
- **Toggle Button**: Switches between ON and OFF states when clicked. Commonly used to control Boolean-type devices, such as start/stop or on/off switches.
- **2-State Button**: Represents two distinct states, typically ON/OFF or Start/Stop. Each state can be configured with specific appearance styles.
- **Multi-State Button**: Contains multiple states and can switch between them. Each state can be configured with its own appearance style.
- **Historical Data Storage of Raw Values**: When storing historical data for variables, it is possible to store the original raw values of the variables.
- **Screen Functions and Expression Functions**: By defining screen functions or expression functions, common logic can be centralized and reused. This avoids writing the same logic repeatedly in each component, allowing one modification to take effect globally, reducing maintenance costs.
- **Binding Support for Enabling/Disabling Animations**: When configuring animations for components, the enabling and disabling of animations can be controlled through property bindings.

#### 4.2.X

- **Permissions**：Supports single sign-on; allows setting permissions for projects and pages.
- **SQL Query**：Enables querying data from third-party databases. It is a pre-configured query that can be later bound to controls. When executing SQL statements, parameters can be passed to return dynamic result sets.
- **Table Control**: Displays data in a table format. You can customize the table’s content, style, and interactive effects.
- **Bidirectional Binding**：Tags, indirect tags, and properties support bidirectional binding. For example, if a control is bound to a tag, changes in the tag will be reflected in the control, and modifying the control’s value will also update the tag.
- **Parameterized Data Source Binding**：When binding a data source to a tag, parameters can be used to replace path content. Later, modifying the parameter value will automatically update the path.
- **Batch Editing Control Properties**：For the same type of controls, such as multiple labels, selecting all of them allows batch modification of their properties.
- **Editable System Tags**：System tags can be edited and configured for alarms, historical storage, and other settings.
- **OPC UA**：Add discovery service function.
- **Camera**: Configure WebRTC Streamer to set up the camera, enabling camera streaming while keeping it separate from the VC Hub server.
- **WeCom and DingTalk support to receive alarm notification**: Support to send alarm notification to WeCom group, WeCom account, DingTalk group , DingTalk account.

#### 4.1.X

- **Alarm Notifications**: VC Hub can send alarm notifications to specific users when a system alarm occurs. Notifications can be sent via email or SMS.
- **Symbols**: Symbols can be used to create detailed models of devices or systems, supporting combinations of multiple components and sub-symbols. This allows users to easily monitor the overall system operation. VC Hub supports user-defined symbols, enhancing operational efficiency.
- **Workspace Upgrades**: VC Hub supports upgrading historical workspaces to the version of the currently installed package.
- **Open API**: VC Hub allows data to be shared with external applications or partners via APIs for seamless data sharing.
- **Property Binding**: Added support for "Dynamic Tag" binding and "Cell Update" binding.
- **Batch Operation Tags**: VC Hub supports bulk addition and editing of tags through Excel.
