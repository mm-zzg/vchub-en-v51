# Devices

 The VC Hub supports a wide range of communication protocols, so you only need to configure the appropriate communication driver for each hardware device.

 To quickly connect to one of your devices, click on the "Devices" menu of the VC Hub and select the type of device you want to add.

## **Supported Device Types**

- [Modbus TCP](modbus-tcp/index.md)
- [Modbus RTU](modbus-rtu/index.md)
- [OPC UA](opc-ua/index.md)
- [MQTT Native](mqtt-native/index.md)
- [MQTT SparkplugB](mqtt-sparkplugb/index.md)
- [SIEMENS S7](siemens-s7/index.md)
- [WAGO Protocol](wago-protocol/index.md)

![alt text](1.png)


## **How do I get data from my PLC?**

 The process of getting data from a PLC into VC Hub is divided into two steps:

1.  Add the device.
2.  Add the I/O tag in the Assets window of the editor. Bind a data source to the tag and select the device you added in step 1 in the data source. See the "Creating Tags" page.
3.  Bind a data source to the tag and select the device you added in step 1 in the data source. See the "[I/O Tag Binding Data Source](../assets-and-tags/tag/creating-tags/io-tag-binding-data-source.md)" page.

![alt text](2.png)

