# Checkbox

The checkbox control represents the switching of two states. By setting the check box to the selected or unselected state, the user can easily switch the state of the corresponding function.

![alt text](18.png)

**Properties**

| **Name**     | **Description**  |
|--------------|------------|
| Name         | The name of this control. |
| X            | The distance between the left side of the control and the left side of the canvas.  |
| Y            | The distance between the top of the control and the top of the canvas.  |
| W            | The width of the control.  |
| H            | The height of the control.  |
| Selected     | The selected state of the control.  |
| Fill         | The fill color of the control. <br>![alt text](19.png)  <br>The text content displayed by the control.  <br>![alt text](20.png)  |
| Border Color | The border color of the control.  <br>![alt text](21.png) |
| Shadow       | Sets the shadow effect of the control. You can set the outer shadow and inner shadow.  <br> **Outer**   <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br> **- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br> **- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br> **Inner**  <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br>**- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br>**- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br>  **- Spread**: Controls how much the shadow **expands or contracts** from the shape. |
| Font         | Set the font for text content. Including font type, font size, font color, bold, italic, underline, horizontal alignment, and vertical alignment.  |

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example**

Automatic operation mode of the factory line can be enabled or disabled via checkboxes. When the check box is checked, the device is started; when the check box is unchecked, the device is stopped.

![alt text](22.png)

1. Add a check box control on the page, and the control name is "Device1".
2. To set mouse event for this control, write the following script.

    ```typescript
    const device1 = await System.UI.findControl('Device1');
    const deviceStatus = device1.selected;
    System.Tag.writeValue('@device:deviceA', deviceStatus ? 1 : 0)
    ```
 
