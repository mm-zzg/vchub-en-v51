# Tag List

The tag list is used to display the names and current values of multiple tags.

![alt text](30.png)

**Properties**

| **Name**          | **Description**          |
|-------------------|----------------|
| Name              | The name of this control. |
| X                 | The distance between the left side of the control and the left side of the canvas.   |
| Y                 | The distance between the top of the control and the top of the canvas.   |
| W                 | The width of the control.  |
| H                 | The height of the control. |
| Data              | Click the Bind button to bind data to the control. Double-click the tag in the Select Tag window to bind it. After binding a tag, if the data type of the bound tag is numeric, you can click the Set button to set the number of decimal places displayed by the tag.                 |
| Refresh Frequency | Set the update frequency of this control's data. The frequency can only be set when enabled.   |
| Fill              | Set the background color of the content display area. <br>- **Background**: Set background color of the control.   <br>- **Odd Rows**: Set background color of the add rows.  <br>- **Even Rows**: Set background color of the even rows. | 
| Border            | Set the border color and border thickness.   |
| Font              | Set font type, font size, bold, italic, and font color.    |


**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example**

Check the production line capacity.

1. Insert a "Tag List" control on the page.
2. Set the control's properties.

| **Property**      | **Value**    |
|-------------------|-------------------------------------|
| Background        | f48256    |
| Odd Rows          | 95c78c  |
| Even Rows         | 84d0e0  |
| Border            | 008080   |
| Font              | Microsoft Yahei, 16, ffffff   |
| Data              | Click the data binding button and double-click the binding tag.  <br>![alt text](31.png) |
| Refresh Frequency | Turn on, set frequency to 1 second.  |

3.Check the display effect.<br>
    ![alt text](32.png)

