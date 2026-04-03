# Text Input

The text input is used to enter any single line of text for writing values.

![alt text](7.png)

**Properties**

| **Name**         | **Description**|   
|-----------|--------|
| Name             | The name of this control. | X                | Distance of the left side of the control from the left side of the canvas.|
| Y                | The distance from the top of the control to the top of the canvas. |
| W                | Width of the control. |
| H                | The height of the control.  |
| Text             | The  text to be displayed in the input text. |
| Password         | Not enabled by default. When turned on, the text entered in the text box displays the cipher text. |
| Fill Color       | The fill color of the input text. |
| Border Color     | The border color of the  input text. |
| Border Thickness | The border thickness of the  input text.  |
| Shadow           | Sets the shadow effect of the control. You can set the outer shadow and inner shadow.  <br> **Outer**   <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br> **- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br> **- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br> **Inner**  <br>**- Enable**: Whether to enable the shadow effect  <br>**- Color**: Used to set the shadow color <br>**- X**: Controls how far the shadow is shifted horizontally.  <br>`X = 10` → shadow moves 10px to the right  <br>`X = -5` → shadow moves 5px to the left <br>**- Y**: Controls how far the shadow is shifted vertically.  <br>`Y = 8` → shadow moves 8px downward  <br>`Y = -3` → shadow moves 3px upward <br>**- Blur**: Controls how soft or sharp the edges of the shadow appear. Higher values make the shadow more blurry and spread out. <br> - **Spread**: Controls how much the shadow **expands or contracts** from the shape. |
| Font             | Sets the font of the input text. Including font, font size, font color, bold, italic, underline. Horizontal alignment: left, center, right.  |

**Event**

Allows you to perform a specific event based on certain conditions. See the [Event](../../event/index.md) page for a complete description of the various events.

**Example**

Modify a device parameter using the input text.

![alt text](8.png)

1. The control appearance is as follows:

    | **Property** | **Value**                          |
    |--------------|----------------------------------------|
    | Name         | Text Input 1                           |
    | Text         | Binding tag: Area.SN                 |
    | Fill color   | 2ef6a3                                 |
    | Font         | Calibri, 22 , Bold, 000000, Left align |

2.In the Evnet property of the control, select "Text Changed", select  "Set Value" as action type, tag is bound to: Area.SN, and new value is bound to: TextInput1#text.

   ![alt text](31.png)

3.On the running page, enter the content in the text input, and the entered content will be written to the tag: Area.SN.