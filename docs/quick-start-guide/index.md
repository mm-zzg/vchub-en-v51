# Quick Start Guide

## 1. System Requirements

Recommended hardware configuration

- x86 64bit, 4 cores
- 16 GB RAM
- SSD with at least 10G free space (pending in the database)

Supported Operating Systems

- Linux (support for popular distributions, tested with Debian and Ubuntu)
- Windows 10/11
- Windows Server 2019/2022

Supported Browsers

- Google Chrome (Latest Version)
- Microsoft Edge (Latest Version)

## 2. Download installation package

Download the latest VC Hub version from the WAGO Download Center.

https://downloadcenter.wago.com/wago/software

There are two versions available for download: **Linux** and **Windows**. 

You can download whichever one suits your actual needs.  

 ![alt text](13.png)

 ![alt text](14.png)

Upload the installer package to the desired computer.

The easiest way is to use a file transfer tool such as WinSCP or FileZilla.
 
![alt text](15.png)

**Be ensured before installation:**
- The device must be accessible to the operator / administrator on the network. At the latest when the application has been installed on the target system, all further steps are carried out via the VC Hub web interface.
- To install the VC Hub, the technician requires administrative rights, meaning they must be a member of the root / sudo group on the target system.
- The target computer requires access to the Internet, as any packages that are not available during installation will be installed automatically. Access to the Internet is also required after installation for licensing the system with the Wago registration server. After that, Internet access is no longer necessary.

## 3. Install VC hub

### 3.1 Windows Environment

**Recommended Systems**

- Windows Server 2012 R2
- Windows Server 2016
- Windows Server 2019
- Windows Server 2022
- Windows 10 (Not supported in Home Edition)
- Windows 11 (Not supported in Home Edition)

**Installation Steps**

1. Run the installation package program as an administrator.

2. Select the installation language.

3. Perform a port check, if the port is occupied, the installation cannot proceed.
  ![alt text](16.png)
4. Read and accept the license agreement.

5. Choose the installation location.

6. Select the VC Hub application data directory.

7. The installation process will take a few minutes. 

8. The installation is complete. Check the Checkbox as shown in the picture below, then click "Finish”. 
   ![alt text](17.png)
9. You will enter the process of creating the user interface. Create an administrator user. Remember this username and password, as you will use them to log in for the first time.
   ![alt text](18.png)
10.	Port configuration.The VC Hub suggests ports 8066 and 10443 for the web interface.
   ![alt text](19.png)
11.	After completing the above steps, wait for the program to load, and then you can log in to the default-created workspace with the user created in step 1.
   ![alt text](20.png)

**Notes:**
With https, only a self-signed certificate is currently available, which is why a security message appears in the browser. This can be adjusted later. It will not affect the current use of the system.

_The IP address is based on the actual deployment address you have chosen. The following image is merely for illustration purposes._

![alt text](21.png)

### 3.2 Linux Environment

**Installation Steps**

1. To perform the installation, you need a Terminal (SSH) connection to the target server. You can log in using a connected display and keyboard, or connect remotely using any SSH tool.
e.g. `ssh root@192.168.1.55` (Server IP or Hostname)
    ![alt text](22.png)
    ![alt text](23.png)
    ![alt text](24.png)
2. For a WAGO Edge Computer server that has a preinstalled operating system, the terminal is also accessible via the web interface.
    ![alt text](25.png)
3. The user performing the installation requires root privileges on the system
    ![alt text](26.png)
4. Install the installation package
    ![alt text](27.png)
5. The installation should be complete after a few minutes. The next steps are taken in the web browser.( The information about the local host is not entirely correct, as the VC Hub can now also be accessed via the configured IP address or the assigned domain name.)
    ![alt text](28.png)
6. Open the URL 192.168.1.55:55:8066, where the address 192.168.1.55 is used here as an example. Use the IP address or domain name you have assigned. Port 8066 must also be specified.
    ![alt text](29.png)
7. Accept the License Agreement.
    ![alt text](30.png)
8. Setting up the first administrator user 
    ![alt text](31.png)
9. Port configuration.The VC Hub suggests ports 8066 and 10443 for the web interface.
    ![alt text](32.png)
10.	Now we can log in with the user we created earlier.
    ![alt text](33.png)

**Notes:**

With https, only a self-signed certificate is currently available, which is why a security message appears in the browser. This can be adjusted later. It will not affect the current use of the system.

_The IP address is based on the actual deployment address you have chosen. The following image is merely for illustration purposes._

![alt text](34.png)

### 3.3 Firewall Settings

#### 3.3.1 Why the Web Interface Cannot Be Accessed

If the web interface cannot be accessed via the selected port, it is highly likely that the host operating system's firewall is blocking the selected port.

Linux firewall mechanisms are very efficient, but configuring rules and port access requires some experience.

For security reasons, it is strongly recommended to block all incoming connections by default and explicitly allow only the ports that are required.

#### 3.3.2 Linux Firewall Overview (UFW)

Many Linux distributions now deliverd with the so called UFW (Uncomplicated Firewall) tool pre-installed.

UFW simplifies the process of setting up the firewall. 

If the tool is not pre-installed, you can easily install it with the command `apt install ufw` or `sudo apt install ufw`.

To do this, the server needs an internet connection and the user performing the installation must do so as root or with root privileges.

![alt text](35.png)

#### 3.3.3 Configuring the Firewall Using UFW 

1. Check UFW status. After installation, UFW is typically inactive.

`ufw status`

2. Deny all incoming connections by default. This blocks all inbound traffic unless explicitly allowed.

`ufw default deny incoming`

3. Allow all outgoing connections by default. This ensures the system can initiate outbound connections.

`ufw default allow outgoing`

4. Allow SSH before enabling UFW.

If you are connected via SSH, this step is critical to avoid locking yourself out.
`ufw allow ssh `
UFW recognizes standard services like ssh.
Alternatively, you can allow SSH by port number:
`ufw allow 22`
5. Enable UFW
`ufw enable `
When prompted, type y and press Enter to confirm.
6. Verify firewall status and rules
`ufw status`
You should now see UFW status as active.
   ![alt text](36.png)
If we have done everything correctly, we can no longer access the web interface of the VC Hub.
   ![alt text](37.png)
You can find very good and detailed instructions on configuring UFW here:
`https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-debian`
   ![alt text](38.png)

#### 3.3.4 Allowing Web Access Ports

Allow HTTP and HTTPS traffic

Allow http (port 80):

`ufw allow 80`

Allow https (port 443):

`ufw allow https`

After enabling these rules, both HTTP and HTTPS access should work again in the web browser.

Allow Additional Ports (Example)

If you use other services or custom ports, you must allow those ports as well.

For example, you may need to enable port 9090 for the Debian web interface:

`ufw allow 9090`











We have outlined some simple steps to guide you through configuring your project. You can run a project in a short amount of time.

## 1.Create a Project

Click the "Add" button in the project list to create a project.

![alt text](1.png)



## 2.Add a Database

After the installation of VC Hub, a SQLite database will be automatically created, which you can use for basic testing. You can also click "[Database](../management-platform/databases/index.md)" -> "[Database Connection](../management-platform/databases/database-connection/index.md)" page and then click the "New" button to create a new database connection. 

## 3.Add Assets

After the installation of VC Hub, a default asset will be automatically created, which you can use for basic testing. You can also click "Tags" -> "[Assets](../management-platform/assets-and-tags/asset/index.md)" page and then click the "New" button to create new assets.

## 4.Open the Editor

On the project list page, click the "Design" button for the project.

![alt text](2.png)


Open the configuration editor to display the following interface.

![alt text](3.png)


## 5.Create a New Page

Click "New Page" to quickly create a new page.

![alt text](4.png)



In the **Tools** window on the left side of the designer, add for example "Rect" , "Label" , "Value Display",and "Historical Trend Chart" controls to the page. You can also use the search functionality.

![alt text](5.png)


## 6.Create a Tag

In the asset dropdown box of the asset window in the configuration editor, select an asset and then click the add button to add a memory tag to that asset. Tag name: liquid.

![alt text](6.png)



Enable the simulated property for this tag, using simulated value as the tag value. Types supported are **Random**, **Increment**, **Decrement**, and **Fixed.**

![alt text](7.png)



## 7.Enable History for Tags

At the top of the tag editing page, enable [history](../management-platform/assets-and-tags/tag/tag-properties/history.md) to store the value of the tag historically.

![alt text](8.png)



## 8.Bind Tag

Bind tags to controls on the page.

1. Set the display content of the text label to: "Liquid level:"
    ![alt text](9.png)
2.  In the animation of the rectangle, select the fill animation. Click the value binding button and bind the created tag:liquid.
    ![alt text](10.png)
3. In the value display control, click the value binding button and bind the created tag:liquid. Afte binding, the binding icon will turn from gray to green.
    ![alt text](11.png)
4. In the historical chart control, click the value binding button and bind the created tag:liquid. 
    ![alt text](12.png)
    
**Note:** For more information on binding, please refer to the Property Binding page. 

## 9.Preview/Run

Click the preview button in the page tool bar to view the preview effect. You can also click the run button for the project in the project list to view the running page.


![quick-start-guide](../assets/images/quick-start-guide.gif)







