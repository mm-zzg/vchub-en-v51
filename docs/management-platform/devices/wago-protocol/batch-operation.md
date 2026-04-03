# Batch Operation of WAGO Protocol Devices

In industrial settings, it is often necessary to create multiple devices in bulk. VC Hub enables this through its export and import functions.

**Note:** To quickly create devices, it is recommended to first manually add a device to the list. Then, export the device and use the exported fields as a reference to add new devices.

## Batch Addition

#### 1.Export Devices

Click the "Export" button in the upper right corner of the list to export all device information.

**Example of an Exported File:**

![alt text](8.png)


- The content inside the red box represents the field information.

#### 2.Adding Devices in Excel

Select the devices, then drag the mouse to quickly copy.

![protocol](../../../assets/images/protocol.gif)


#### 3.Import Devices

Click the "Import" button in the upper right corner of the list to import the exported content. After importing, the newly added devices will have their enabled status set to "Disabled" by default.

![alt text](9.png)


## Batch Modification

You can batch modify device information through the exported Excel file. After making modifications, import the Excel file, and the data will be updated based on the device name.

- If the device name in Excel matches the name in the WAGO Protocol list, the corresponding configuration from Excel will be used to update the data.
- If the device name in Excel does not exist in the WAGO Protocol list, a new device will be added to the list.
- If a device name in the WAGO Protocol list does not exist in the import file, the data in the list will remain unaffected after the import.

## Batch Deletion

After selecting the devices to be deleted, click the **Delete** button at the top of the list to perform batch deletion.

![alt text](10.png)


Notes:

- Devices that are **Enabled** cannot be deleted.
- Only devices on the current page can be deleted; cross-page deletion is not supported.
