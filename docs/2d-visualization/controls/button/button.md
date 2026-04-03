# Button

Buttons are used to initiate an event when pressed and can also be used to display status.

![alt text](1.png)

**Properties**

| **Name**   | **Description**      |
|-----------|-----------------------|
| Name  | The name of this control.   |
| X  | The distance between the left side of the control and the left side of the canvas.  |
| Y   | The distance between the top of the control and the top of the canvas.   |
| W | The width of the control.  |
| H   | The height of the control.  |
| ![alt text](2.png) | The rounded curvature of the four corners of the button. |
| Fill   | The content displayed by the control.  <br>![alt text](3.png)  <br>![alt text](4.png) <br>The button's background image. Only JPG, GIF, PNG, SVG, and JPEG formats are supported.  |
| Border  | The color and  thickness of the border.   |
| Shadow    | Sets the shadow effect of the control. You can set the outer shadow and inner shadow.  <br> **Outer**   <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br> **- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br> **- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br> **Inner**  <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br>**- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br>**- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br>  **- Spread**: Controls how much the shadow **expands or contracts** from the shape. |
| Color   | Set the color effects for different operational states of a control. The states include: default, hover, and pressed.   You can set the background color, border color, and font color for each state.  ![alt text](5.png)   |
| Font     | Set the font for text content. Including font style, font size, font color, bold, italic, horizontal alignment, and vertical alignment.  |

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example**

Click the button to navigate to other page.

![alt text](6.png)

| **Property**  | **Value**     |
|---------------|---------------|
| W   | 80                                                    |
| H   | 32                                                    |
| ![alt text](7.png) | 4       |
| Background    | 1c1c88                              |
| Text     | < Back          |
| Font    | Calibri, 22, horizontal centering, vertical centering |

On the button, add a press event, select 'Navigation' as the operation type, choose 'Page1' as the page, and select 'Replace ' as the open position. On the runtime page, clicking this button will navigate to Page1.

![button](../../../assets/images/button.gif)



