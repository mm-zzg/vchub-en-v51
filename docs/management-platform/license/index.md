# License

VC Hub uses licenses to activate features on the VC Hub server. At the moment, only **online activation** is supported.

## Trial Mode

After installing VC Hub, the system automatically enters a **30-day trial period**. During the trial period, all features are fully available.

When the trial period expires:

- The **Admin Console** and **Designer** pages will remain accessible.
- **Driver data acquisition will stop**.
- The **Preview** and **Runtime** pages will display a message indicating that the trial has expired.

After the trial expires, you may:

-  **Enter a trial license again** to start another 30-day trial, or
-  **Purchase the appropriate feature licenses** to restore full functionality.

### Trial Countdown

The 30-day trial countdown starts **immediately after the installation** of VC Hub.

![alt text](36.png)


### Trial Expired

After the trial period expires, the preview and the running page will be forced to jump to the "Trial Expired" interface.

![alt text](37.png)


### Trial Extension

After the trial expires, you can enter another trial license (please contact Sales to obtain one) to extend the trial period for an additional 30 days.

You can also enter a new trial license **before** the current trial ends. Regardless of how many days remain, once a new trial license is applied, the trial countdown will automatically reset to 30 days.

## Operating License

For a detailed introduction of "license" type, please refer to [License](../installation/product-license.md).

### Activate

**Activation Steps:**

1. Click the menu "Node"->"License", and click on the "Activate License" button at the top right corner of the list.
![alt text](38.png)
2. Fill in the key and click the "Activate" button.You can input one or more keys at a time.
![alt text](39.png)
3. After successful activation, the license list will show the license information. For activated keys, you can perform deactivate and update operation.
![alt text](40.png)

**Notes:**

1. In the license list, the License Type must be the same.
2. For the same License Item, only one activated license is allowed.
3. After activation, the license key will be **bound to the installation server**, and the same key cannot be activated on multiple servers.
4. Once any license in the license list has a remaining validity period of 30 days or less, a license expiration reminder will be displayed in the top-right corner of the Admin Console and Designer pages.

    ![alt text](44.png)

### Deactivate

A license that is in the activated state can be deactivated.

![alt text](41.png)

If you wish to remove the license from the current machine and use it on another machine instead, you must first perform a **deactivate** action. After deactivation, the corresponding license will be removed from the current machine. 

You can reactivate it on another machine or on the current one again.

After reactivation, the validity period of this license remains unchanged and is still the same as it was before deactivation.

Unless necessary, please avoid using the deactivation function frequently.

### Delete

A license that is in the expired state can be deleted.

![alt text](45.png)

After clicking the Delete button, the license will be removed from the list.

### Refresh

You can refresh the license information at any time. After refreshing, the latest status of the license will be retrieved.

![alt text](42.png)

### Renewal

If you would like to continue using the license before it expires, please contact the sales support to renew the license.You only need to refresh the license information to obtain the updated validity period.

Please complete the renewal before the license expires. Once the license expires, the corresponding functionality will become unavailable, which may impact your production environment.

### Update

When you want to change the number of **I/O tags** or **concurrent online users**, you can use the **Update** operation.

![alt text](43.png)

Only one license can be activated for each license item at a time. Normally, to change a license, you need to deactivate the existing license first and then activate a new one. For I/O tag licenses, deactivation will stop data acquisition, which may cause temporary data loss in a production environment.

By using the Update operation, you can avoid this issue and modify the license without interrupting data acquisition.

However, please note that if you attempt to update using an invalid license (for example, an already activated or expired license), the update will fail and may result in the loss of the license for that module.

Therefore, please perform this operation with caution.

## License Expired

When the license expires:

- The **Admin Console** and **Designer** pages will remain accessible.
- **Driver data acquisition will stop**.
- The **Preview** and **Runtime** pages will display a message indicating that the license has expired if an unauthorized control is used on the page. For example, the licenses for 3D and Report have expired.

    ![alt text](46.png)

## License Verification

After a user logs in, the system will display the corresponding interface based on the activated license status.

- If no license is activated, the system will enter trial mode, in which all features are available.
- If a license is activated, the system will display features according to the license type.

Specific limitations include:

- If no license for concurrent online users is activated, the system supports only 1 engineering user and 10 runtime users logged in simultaneously.

- If no license for I/O tag types is activated, all data collection and publishing will stop on the runtime pages.

- For any unlicensed modules, a “Module Not Licensed” message will be displayed. For example, as shown below, the MQTT module is not licensed.

![](47.png)

### Distinguishing Between Engineering Users and Runtime Users

When a concurrent online user license is activated, users must be distinguished as either engineering users or runtime users during login.

When the number of users has not reached the limit:

- Engineering users will be directed to the Admin Console page after login.

- Runtime users will be directed to the runtime view after login.

When the user limit is reached, refer to the Concurrent Online User section in [License](../installation/product-license.md) for details.


#### Configuring Accessible Runtime Views for Runtime Users

Runtime users **must have a role** in order to access runtime views.

The configuration steps are as follows:

**For users with Local Identity Provider**

1. Create a project "ProjectA", and create a page named "Home" under this project.

2. Create a role (e.g., test) and set its Startup Page to "ProjectA.Home".

3. Create a user (e.g., Alex) and assign the role "test".

4. In the project list, click the Design button for "ProjectA". In the opened editor, right-click the page "Home" in the Project panel, set its Permission, and select role "test" in the Access Level tree.

5. Log in as Alex. The Home page will be displayed automatically after login.


**For users with OpenID Connect Identity Provider**

1. Based on the current Identity Provider, create the same role in VC Hub.

2. Add the Identity Provider in VC Hub.

3. Configure **User Attribute Mapping** for the Identity Provider in VC Hub.

4. Configure **User Grants** for the Identity Provider in VC Hub, and add a user (e.g., Jane). (Note: The username must match the one in the Identity Provider. Set the user type to Runtime User.)

5. Create a project ProjectA, and create a page named "Home" under this project.

6. In VC Hub, set the Startup Page of role test to ProjectA.Home. (Note: The user Jane has the role test in the Identity Provider.)

7. In the project list, click the Design button for ProjectA. In the editor, right-click the page "Home", set its Permission, and select "test" in the Access Level tree.

8. Log in as Jane. After accessing VC Hub, the Home page will be displayed automatically.



















