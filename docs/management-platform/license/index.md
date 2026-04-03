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

## Trial Countdown

The 30-day trial countdown starts **immediately after the installation** of VC Hub.

![alt text](36.png)


## Trial Expired

After the trial period expires, the preview and the running page will be forced to jump to the "Trial Expired" interface.

![alt text](37.png)


## Trial Extension

After the trial expires, you can enter another trial license (please contact Sales to obtain one) to extend the trial period for an additional 30 days.

You can also enter a new trial license **before** the current trial ends. Regardless of how many days remain, once a new trial license is applied, the trial countdown will automatically reset to 30 days.

## Activation

After activation, the license key will be **bound to the installation server**, and the same key cannot be activated on multiple servers.

For a detailed introduction of "license", please refer to [License](../installation/product-license.md).

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
3. Once any license in the license list has a remaining validity period of 30 days or less, a license expiration reminder will be displayed in the top-right corner of the Admin Console and Designer pages.

    ![alt text](44.png)

## Deactivation

A license that is in the activated state can be deactivated.

![alt text](41.png)

If you wish to remove the license from the current machine and use it on another machine instead, you must first perform a **deactivation** action. After deactivation, the corresponding license will be removed from the current machine. 

You can reactivate it on another machine or on the current one again.

After reactivation, the validity period of this license remains unchanged and is still the same as it was before deactivation.

Unless necessary, please avoid using the deactivation function frequently.

## Delete

A license that is in the expired state can be deleted.

![alt text](45.png)

After clicking the Delete button, the license will be removed from the list.

## Refresh

You can refresh the license information at any time. After refreshing, the latest status of the license will be retrieved.

![alt text](42.png)

## Renewal

If you would like to continue using the license before it expires, please contact the sales support to renew the license.You only need to refresh the license information to obtain the updated validity period.

Please complete the renewal before the license expires. Once the license expires, the corresponding functionality will become unavailable, which may impact your production environment.

## Update

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









