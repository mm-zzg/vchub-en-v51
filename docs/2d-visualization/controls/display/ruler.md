# Ruler

Ruler is used to measure and mark lengths, often used with text label controls.

![alt text](78.png)

**Properties**

| **Name**   | **Description**  |
|--|-------------------|
| Name| The name of this control. |
| X   | The distance between the left side of the control and the left side of the canvas.  |
| Y | The distance between the top of the control and the top of the canvas.   |
| W | The width of the control.   |
| H | The height of the control.   |
| ![alt text](79.png) | The angle of the control.  |
| Fill  | The background color of the control.  |
| Tick  | Sets the appearance style of the tick.  <br> - **Axis**: Set the axis color. The red area in the figure below is the main axis. <br>![alt text](80.png) <br> - **Major Tick**: Set the major tick color, quantity and length. The red area in the figure below is the major tick. <br>![alt text](81.png) <br> - **Minor Tick**: Set the minor tick color, quantity and length. The red area in the figure below is the minor tick.  <br>![alt text](82.png) |
| Tick Value    | Set the measuring range of the ruler.  <br> - **Show**:  Whether or not to display the value.  <br> - **Reverse**: Displays the maximum and minimum values of the ruler values in reverse.  <br>Before reverse: <br>![alt text](83.png)  <br>After reverse: <br>![alt text](84.png)   <br> - **Min**: Minimum value of the ruler <br> - **Max**: Maximum value of the ruler <br> - **Type**: Contains value and percentage to set the numeric type  <br> - **Decimals**: Sets the number of decimal places for the ruler value.     <br> - **Font**: Sets the font type, font size, bold, italic, and font color for the ruler value.  |
| Indicator    | Set the style for each indicator on the ruler. Available styles include Arrow, Line, and Wedge.   Click the Settings button to open a dialog where you can configure the indicators and their styles. ![alt text](85.png) <br> - **Indicator Value**: Value corresponding to the indicator   <br> - **Style**: Select the style for the indicator , choosing from arrow,  line, or wedge <br> - **Color**: Set the color of the indicator <br> - **Extend**: When "Line" is selected, the Extend field is disabled.  <br>![alt text](86.png) <br> - **Length**: The overall length of the indicator <br> - **Width**:  <br>When **Wedge** is selected, the Width field is disabled. <br> When **Line** or **Arrow** is selected, the Width value represents the width of the line segment. <br> - **Offset**: Setting the distance between the indicator and the axis <br> - **Label**:  Set a text label for the indicator <br> - **Label Angle**: Set the text’s display orientation <br> - **Label Color**: Set the font color of the text  |

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example**

Add 3 indicators to the ruler to indicate the max, min and avg values.

1. Insert a ruler control on the page
2. Click on the control and in the Appearance property of the control click on the setting button of the indicator 

    ![alt text](87.png)

3. Make the following settings in the datatable popup window

    ![alt text](88.png)

4. After saving the popup, the ruler is displayed as follow：

    ![alt text](89.png)



