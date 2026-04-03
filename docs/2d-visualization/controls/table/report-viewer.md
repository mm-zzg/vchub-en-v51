# Report Viewer

The Report Viewer is used to display reports that have been created in the Report Editor.

![alt text](33.png)

**Interface Elements**

![alt text](34.png)

**Properties**

| **Name**    | **Description**   |
|-------------|-----------------------------------|
| Name        | The name of this control.  |
| X           | The distance between the left side of the control and the left side of the canvas.  |
| Y           | The distance between the top of the control and the top of the canvas. |
| W           | The width of the contro.   |
| H           | The height of the control.   |
| Report      | Select the report data you want to view.  |
| Background  | Set the background color of the control.   |
| Border      | Set the border color and border thickness.       |
| Report List | Set the appearance style of the report list.  <br>- **Show**: Control the display and hiding of the report list. <br>- **Width(px)**: Set the column width of the report list.      <br>You can also set the background and font of the text information in the report list in different selected states. Contains two states: default and selected.  <br>![alt text](35.png) |
| Tool Bar    | Set the style of the toolbar.   <br>- **Default Show**: Control the display and hiding of the toolbar's default state.  <br>- **Background**: Set the toolbar background color.              <br>- **Button**: Set the color of each button in the toolbar.      |
| Adaptation  | When turned on, the report content automatically adapts to the size of the control. When it is turned off, if the actual size of the report exceeds the size of the control, scroll bars will be displayed in the corresponding direction.   |

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example**

View the report.

1. Insert a "Report Viewer" control on the page. Set the following properties.

| **Property** | **Value**   |
|--------------|-----|
| Report List  | - Selected background: 99e699  <br>- Selected Font: Microsoft Yahei, 14, bold, f0672e | 
| Report       | Line 1   |

2.Click the "Preview" button on the page.<br>

3.In the report viewer, click "Line 1" to view the data.
    ![alt text](36.png)

