# Quality

Quality is used as an property of a tag to indicate the level of confidence in the value of the tag. The quality of the tag is reflected by the quality level code.

The quality bit code consists of a level ("Good", "Uncertain", "Bad", "Error ") and an integer. If a value is bad quality, it should usually not be trusted .

You can view the quality of a tag in the Asset window by locating the tag you wish to view and expanding it. The following image shows a tag whose quality bit is Good, which means that the tag's current value is trusted.

![alt text](2.png)

## **Quality Codes**

There are currently four levels of quality codes set up in the system, Good, Bad, Uncertain and Error, and each level contains a series of sub-codes that will provide more specific quality information about the current tag.

The system divides the quality bits of each level into different code areas as follows:

1. **Good: 100~199**. Good quality, usually considered reliable and trustworthy.
2. **Uncertain: 200~299**. Uncertain quality, usually represents a good value, but the reliability cannot be determined because the new value has not been received. 
3.  **Bad: 300~399**. Bad quality, the value is problematic, but it is the "expected" or recognized type of problem. For example, the trial has expired or read access has been explicitly denied. 
4.  **Error: 400~499**. Error quality, completely unexpected problems. For example, a tag is misconfigured, a type is incorrect, and so on.

**Note:** It is important to note that not every value in the range has a code, and the free values are used for future extensions and adding new codes. 


| **Good**   | **Code(100~199)** | **Description**    | **Example**   |
|-------------|-------------------|--------|------------|
| Good    | 100               | A generic, conforming to a standard considered reliable   | A value that is normally captured and the quality bit is good.  |
| Good_Initial                       | 101               | A tag initial value that can be considered reliable.  | Initial value for the first push after the tag is created.  |
| **Uncertain**    | **Code(200~299)** | **Description**   | **Example**   |
| Uncertain                          | 200               | A generic value with unspecified uncertainty. Currently only adapted to the OPC UA driver.  | The current quality bit code corresponds to code 64, 65, 66, 67 in OPC UA protocol.  |
| Uncertain_LastUsableValue          | 201               | The value of this tag has ceased to be updated by the other party and the current value should be regarded as obsolete. Currently only adapted to the OPC UA driver. | The current quality bit code corresponds to codes 68, 69, 70, 71 in the OPC UA protocol.  |
| Uncertain_DataSubNormal            | 205               | This value requires multiple source data to generate and has fewer good sources than required. Currently only adapted to the OPC UA driver.                          | The current quality bit codes correspond to codes 88, 89, 90, 91 in the OPC UA protocol.  |
| Uncertain_EngineeringUnitsExceeded | 206               | The value has exceeded its configured engineering units. Only the OPC UA driver is currently adapted.   | The current quality bit code corresponds to codes 84, 85, 86, 87 in the OPC UA protocol.  |
| **Bad**                           | **Code(300~399)** | **Description**   | **Example**    |
| Bad                                | 300               | A generic, error value routine code. Currently only adapted to the OPC UA driver.   | The current quality bit code corresponds to codes 0, 1, 2 and 3 in the OPC UA protocol. |
| Bad_NotFound                       | 310               | The requested object does not exist.    | The tag has been deleted and an attempt was made to subscribe to the value of the tag at this time.   |
| Bad_NotSupported                   | 311               | Tag binding is not supported.    | Nodes in OPC Server do not support binding.   |
| Bad_NotConnected                   | 315               | The driver required for the current tag is not connected or the connection is closed.  | The driver did not successfully connect to the device or an error occurred while connecting;  The driver was stopped manually;  The driver is in an unstarted state. |
| Bad_OutofRange                     | 320               | The value of the current tag is outside the engineering upper and lower limits. | If a tag is configured with an engineering upper or lower limit, the tag value is out of range of the upper or lower limit.  |
| Bad_NotLicensed                     | 326               | There is no active I/O tag license. |  The I/O tag license has expired.|
| Bad_MQTTNotLicensed                     | 327               | There is no active MQTT license. This license is used by MQTT Native, MQTT Sparkplug B, and WAGO Protocol devices.|  The MQTT license has expired.|
| **Error**                          | **Code(400~499)** | **Description**  | **Example**   |
| Error                              | 400               | A generic code that indicates an error in the current tag.   | If the error cannot be indicated by other Error codes, the current code is used.   |
| Error_Configuration                | 401               | There is an error in the configuration of the current tag.    | The device to which the tag is bound does not exist.   |
| Error_Expression                   | 402               | The expression that generated the value of this tag was executed incorrectly. | Any error occurred during the expression parsing execution of the expression tag.   |
| Error_TypeConversion               | 405               | The received value could not be forcibly converted to the data type set by the tag.   | Expression data type conversion failed;  The type of the received value does not match the type of the tag and  forced conversion failed.                            |
| Error_Exception                    | 410               | An exception caught during the acquisition of a value by the tag    | Any error that occurred during driver acquisition.   |
| Error_InvalidPath                  | 411               | The path or path syntax of the tag is incorrect.   | The path of a tag on which the expression depends is not legal (does not satisfy the naming rules).                                                                  |

## **The control displays a corner marker**

If a tag is bound to a control, the quality code of the bound value can be rendered by a corner marker. Corner markers are displayed only when the quality is Bad, Uncertain, and Error.

| **Corner**  | **Quality** |
|-------|-------------|
| ![alt text](3.png)| Uncertain   |
| ![alt text](4.png) | Bad         |
| ![alt text](5.png) | Error       |

If the control is bound to multiple tags with multiple qualities, only the highest quality level corner is displayed in the upper right corner of the control. Hover over the corner to display the full message. Hover over the corner to display the full message, as shown in the following figure.

Level: Error>Bad>Uncertain

![alt text](6.png)


