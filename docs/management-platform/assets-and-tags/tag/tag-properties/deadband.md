# Deadband

 By setting the deadband for tags, you can filter the values of pushed tags to exclude meaningless pushed data.

 Only tags of type Integer and Double can enable this configuration.

## **How to Enable**

   In the add or edit  pop-up window of the tag, there is a deadband switch at the top of the popup window, turn it on to set the deadban

![alt text](15.png)

 When it is turned on,the popup window will automatically display the deadband  configuration items,users can set the deadband  according to the actual needs, click **"OK"** button after the setting is completed.

![alt text](16.png)

| **Name**       | **Description**                                                                                                                                                                                                                                                                                                                                                                             |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mode           | There  are two modes:  <br> 1. Absolute:The absolute value of **(New Value-Previous Value)**, whether it is greater than the dead zonevalue, if it is greater, it will be collected, if not, it will be ignored.<br> 2.Percent: The absolute value of **(New Value - Previous Value)** is greater than the deadband value * the absolute value of **(Engineering Upper Limit - Engineering Lower Limit)** / 100, if greater, it will be collected, otherwise, it will be ignored. |
| Deadband Value | Used for the calculation of the acquisition deadband.                                                                                                                                                                                                                                                                                                                                       |

  


