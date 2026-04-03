# Toggle Button

The toggle button control represents the switching of two states. By setting the selected or unselected state, the user can easily switch the state of the corresponding function.

![alt text](31.png)

**Properties**

| **Name**   | **Description**    |
|---------------|-------------|
| Name| The name of this control.   |
| X   | The distance between the left side of the control and the left side of the canvas.  |
| Y  | The distance between the top of the control and the top of the canvas.   |
| W  | The width of the control.  |
| H | The height of the control.  |
| ![alt text](32.png)| The rounded corner curvature of the control.  |
| Selected |
| Border  | The border width of the control.   |
|  | Sets the shadow effect of the control. You can set the outer shadow and inner shadow.  <br> **Outer**   <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br> **- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br> **- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br> **Inner**  <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br>**- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br>**- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br>  **- Spread**: Controls how much the shadow **expands or contracts** from the shape. |
| Color  | Set the background color, border color and font color for the control in both selected and unselected states.  |
| Font | Set the font for text content. Including font type, font size, font color, bold, italic, underline, horizontal alignment, and vertical alignment.    |

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example**

The fan can be turned on or off by using the Toggle Button control. When the Toggle Button is selected, the fan is activated; when the Toggle Button is deselected, the fan is stopped.

1. Add a Toggle Button control to the page, with the control name being "Toggle Button1".
2. Bind the "Selected" property to the tag "Device:status", and enable two-way binding.
3. On the running page, press the Toggle Button to start the fan, and click the Toggle Button again to deselect, thereby stopping the fan.

