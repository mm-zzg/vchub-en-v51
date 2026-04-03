# Real Time Event

Real-time event controls are used to display events as they occur. By default, it displays all events, and the control only supports displaying the latest 2000 pieces of data. You can also set filter conditions.

![alt text](1.png)

You can click and drag a column's margins on the preview and run page to adjust its width. You can also sort columns in ascending or descending order by clicking the up or down arrow next to each column header.

You can also click the pause button to pause data refresh, and query and view the data in the paused state. After clicking the pause button, the resume and query buttons are displayed.

![realtime-event](../../../assets/images/realtime-event.gif)

**Properties**

| **Name**         | **Description**     |
|------------------|------------------|
| Name             | The name of this control.   |
| X                | The distance between the left side of the control and the left side of the canvas.    |
| Y                | The distance between the top of the control and the top of the canvas.  |
| W                | The width of the control.    |
| H                | The height of the control.   |
| Border Color     | Set the color of the outer border of the control and the table line of the table body.    |
| Border Thickness | Set the thickness of the outer border of the control and the table line of the table body.   |
| Table Header     | Set the background color, font type, font size, bold, italic, and font color of the table header.   |
| Table Body       | Set the background color, font type, font size, bold, italic, and font color of the table body.   |
| Color            | Sets the color displayed on the control for each event type.    |
| Button Style     | Sets the style of the buttons used on the control. Click the setting button of the button style to set it.  <br>![alt text](2.png) Pause Button.Background color, border color, font type, font size, bold, italic, and font color of the pause button.   <br>![alt text](3.png) Resume Button.Restore the button's background color, border color, font type, font size, bold, italic, and font color.  <br>![alt text](4.png) Search Button.The background color, border color, font type, font size, bold, italic, and font color of the button.    | 
| Search Style     | Set the background color and border color of the search box, the search title and the font type, font size, bold, italic, and font color of the entered search content.  |
| Column           | Set the column names that need to be displayed on the control.   |
| Sort Order       | Sets how data is sorted on the control.   |

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example 1**

Perform data filtering on the running page.

1. Click the "Pause" button on the running page.
2. Set the query conditions, select the event type: Security, and select the subtype: Login.
3. Click the "Search" button.

![realtime-event1](../../../assets/images/realtime-event1.gif)







