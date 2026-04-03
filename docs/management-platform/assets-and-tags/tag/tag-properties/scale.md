# Scale

 In many cases, the data collected by the device does not meet the actual display requirements, for example, we need to collect the instantaneous power of amotor, the unit of collection is W, and the instantaneous power unit that needs to be displayed on the page  is Kw, then we can convert the collected value to the target value through scale.

 Currently,only I/O tags support scale , and the data type must be Integer,Double or Bool.

**How to Enable**
 In the add or edit  pop-up window of the tag, there is a switch for scale  at the top, which can be turned on to set the specific rules for scale.

![alt text](17.png)

 When the switch is turned on, the range conversion configuration will be automatically displayed in the popup window, users can set the range conversion configuration according to the actual needs, and click the **"OK"**  button after the setting is completed.
![alt text](18.png)

| **Name** | **Description**                                                                                                                                                                                                                                                                         |
|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mode     | There  are 3 modes:  -  Linear:This mode is displayed when the data type of the tag is Integer, Double. -  Square: This mode is displayed when the data type of the tag is Integer,Double. - Re verse:This mode is displayed when the data type of the tag is Bool.                     |
| Raw      | Configurable when the mode is Linear or Square.   <br>![alt text](19.png) |
| Value    | Configurable when the mode is Linear or Square.  <br>![alt text](20.png)  |

## **Formula**

#### **Linear**

 Displayed value = Min value + (Current raw value - Min raw value) * (Max value  - Min value) \ (Max raw value - Min raw value )

#### **Square**

 Displayed value = Min value + √(Current raw value -Min raw value) * (Max value - Min value)\ √(Max raw value - Min raw value ) 

 **Note:**  √  means square

#### **Reverse**

-  When the captured value is True, the actual displayed value is False;
-  When the captured value is False, the actual display value is True.


