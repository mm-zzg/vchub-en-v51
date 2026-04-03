# Value Display

Value display control is used to display data, which can display numerical, boolean, string and datatime data.

![alt text](11.png)

**Properties**

| **Name**   | **Describe**     |
|-------|---------|
| Name | The name of this control.  |
| X  | The distance between the left side of the control and the left side of the canvas.  |
| Y | The distance between the top of the control and the top of the canvas.  |
| W | The width of the controlx. |
| H  | Height of the control.  |
| ![alt text](12.png) | The angle of the control. |
| Data   | The data received by the control.  <br> -Text: What needs to be displayed. You can enter it manually or click the binding button to bind.   <br> -Units: Sets the unit of the displayed data. You can enter it manually or click the Bind button to bind it. <br> - Format: The content format is expected to be displayed. You can enter it manually or click the settings button and double-click to select the desired format. |
| Fill  | The fill color of the control.  <br>![alt text](13.png) |
| Font  | Set the font of the control content. Including font , font size, font color, bold, italic, underline, horizontal alignment, vertical alignment.|
| Right Click Menu | Setting the context menu on the control allows you to set the background color, border color, font type, font size, font color, bold, and skew of the menu. You can configure actions for the context menu, including navigation, set value, set property, and script.  On the running page, right-click on the control to display the context menu.  |

**Animation**

Allow you to execute specific animations based on certain conditions. Please refer to the complete description of various animations on the [Animation](../../animation/index.md) page.

**Event**

Allow you to perform specific event based on certain conditions. Please refer to the complete description of various events on the [Event](../../event/index.md) page.

**Example 1**

Display the temperature of the current working environment.

![alt text](14.png)

| **Property** | **Value**     |
|--------------|--------------|
| Fill         | 2c2c2c |
| Text         | Binding tag: Demo:temperature  <br>![alt text](15.png) |
| Units        | ℃    |
| Font         | Calibri, 16, ffffff, horizontal right, vertical center |

**Example 2**

Display the system time.

![alt text](16.png)

| **Property** | **Value**    |
|--------------|---------------|
| Text         | Binding tag: System:Server.CurrentDateTime   |
| Format       | `yyyy-MM-dd HH:mm:ss`             |
| Font         | Calibri, 16, 6ec800, horizontal center, vertical center |

**Example 3**

View Celsius and Fahrenheit temperatures via the right-click menu.

![alt text](17.png)

| **Property**     | **Value**         |
|------------------|------------|
| Text             | expression：  <br>const value = tag(`'@Demo:temperature'`);  <br>if(property('ValueDisplay1#units') === '℃'){      <br>return value;  <br>}  <br>return (value * 9 / 5) + 32; |
| Format           | #,##0.# |
| Font             | Calibri,16, 6ec800，horizontal center, vertical center |
| Right Click Menu | Add two right-click menus: Celsius, Fahrenheit.  In the Fahrenheit action, set the property binding, which displays the value of the control's UNITS property, to set its value to ℉  <br>![alt text](18.png)  In the Celsius action, set the property binding, which displays the value of the control's units property, to set its value to °C  <br>![alt text](19.png) |

Click the Preview button on the page, and on the preview page, right-click the control to toggle the context menu and view the display.

![value-display](../../../assets/images/value-display.gif)

