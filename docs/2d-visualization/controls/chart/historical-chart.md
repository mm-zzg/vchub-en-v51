# Historical Chart

A historical chart is a chart that shows trends in data over a past period of time. The X-axis is the time axis and the Y-axis is the data axis.

![alt text](12.png)

**Properties**

| **Name**     | **Description**   |
|--------------|---------|
| Name         | The name of this control. |
| X            | The distance from the left side of the control to the left side of the canvas, in pixels.  |
| Y            | The distance from the top of the control to the top of the canvas, in pixels.  |
| W            | The width of the control, in pixels.  |
| H            | The height of the control, in pixels.  |
| Time Range   | Query based on the specified time period.  <br>![alt text](13.png)  <br>- **Last**: Set the time range for data display.    <br>- **Custom**: Set the start time and end time to customize the time range for data display.   |
| Query Mode   | Query according to the selected query mode, which includes: Raw, Fixed Points, and Periodic.  <br>- **Raw**: Retrieves all raw historical data within the selected time range. When selecting Raw, the aggregation mode of the tag is disabled. <br>- **Fixed Points**: Requires setting the number of points. The selected time range is divided into corresponding time intervals based on the set number of points, and one data point is selected from each interval according to the specified aggregation mode. <br>- **Periodic**: Requires setting a period. The selected time range is divided into corresponding time intervals based on the set period, and one data point is selected from each interval according to the specified aggregation mode.  |
| Data         | Click the dataset button to set the data source and style for the historical trend chart.  <br>![alt text](14.png) Clicking this button allows you to set the data source and style for the curve.  <br>![alt text](15.png)  <br>- **Tag**: Set the data source for the curve.  You can copy the path of a tag directly to the "Name” column by clicking on the following symbol on the far right of the "Tag" column. <br>![alt text](16.png) <br>- **Name**: Set the name of the curve. <br>- **Y Axis**: Select a Y-axis as the Y-axis of the current tag.<br>- **Line Color**: Set the color of the curve. <br>- **Line Type**: The type of the curve. <br>- **Line Style**: The style of the curve.  <br>- **Line Width**: The width of the curve. <br>- **Area**: Set the background color of the area between the curve and the axis. <br>- **Alarm Line**: Set whether the alarm value of the tag is displayed as a line on the current control.  Click the Set button of the alarm line to select the alarm line to be displayed and set the style for it.  Check the checkbox of t<br>- **Average Line**: Sets whether the average value of the tag over the query time period is displayed as a straight line on the current control. When enabled, you can set the line shape of the average.     <br>- **Average Line Width**: Sets the line width of the average line.  <br>- **Symbol Style**: Set the style of markers on the curve. <br>- **Symbol Size**: The size of the mark. <br>- **Decimals**: Move the mouse to the number of decimal places displayed on the curve.  <br>- **Aggregation Mode**: Set the data aggregation method. This field takes effect when the query type is Fixed Points or Periodic. | |
| Show         | Set the display and hiding of the button.  <br>- **Select Tag Button**: Set the display and hiding of the tag selection button.When visible, this button on the running page allows users to reconfigure the tags and their corresponding curve display styles. <br>- **Export Button**: Set the display and hiding of the export button.When visible, this button on the running page allows users to export the queried data.  <br>- **Search Button**: Control the visibility of the query button. When visible, users can reset the query time range and mode on the runtime page.     |    |
| Button Style | - **Select Tag Button**: Set the color of the tag selection button. <br>- **Search Button**: Set the color of the search button.        <br>- **Export Button**: Set the color of the export button.        |  
| Color        | Set the color effect of the control.  <br>- **Background**: The overall background color of the control. <br>- **Grid**: The line color of the grid.                 <br>- **X Axis**: The axis color of the X Axis.   |    
| Margin       | Set the spacing between the control and its selection box. Ensure that the chart is displayed clearly and sufficient space is reserved for chart elements, such as time or legend. |
| X Axis       | Set the style of the X Axis.  <br>- **Show Grid**: Control the display and hiding of the grid. <br>- **Time Format**: Set the format of the time displayed on the X-axis, you can choose the time format preset by the system or input it manually, the time format set must meet the time format requirements of Echarts.  For details, see  [https://echarts.apache.org/zh/option.html#xAxis.axisLabel.formatter](https://echarts.apache.org/zh/option.html#xAxis.axisLabel.formatter) <br>- **Font**: Set the font, font size, bold, italics, and font color of the text displayed on the X-axis.    |   
| Y Axis       | Set the style of the Y-axis.  <br>- **Show Grid**: Control the display and hiding of the grid. <br>- **Enable Subplot**: Control whether embedding another chart is allowed in the main chart. <br>- **Grid(s)**: Set the number of dividing lines inserted on the Y-axis.              <br>- **Axes**: Display the number of rows and columns of the axis.                   <br>![alt text](17.png) Clicking this button allows you to set the style of the axis.  ![alt text](18.png) <br>- **Name**: The name of the Y axis. <br>- **Auto Range**: The range of the Y-axis changes dynamically according to the range of values. If checked, the value range of the Y-axis will be automatically determined. If unchecked, the min and max values will be used.  When Auto is selected, the min and max values become invalid. <br>- **Min**: Minimum value of Y axis.   <br>- **Max**: The maximum value of the Y-axis.  <br>- **Decimals**: Set the number of decimal places displayed on the Y-axis tick values.  <br>- **Show**: Control the display and hiding of the Y-axis. <br>- **Position**: Set the display position of the Y-axis.  <br>- **Offset(px)**: Set the offset of the Y-axis relative to its default position. <br>- **Axis Color**: Set the color of the Y-axis.    <br>- **Font**: Set the font for the Y-axis labels.   <br>- **Font Size**: Set the font size for the Y-axis coordinates.  <br>- **Font Color**: Set the font color for the Y-axis coordinates.  <br>- **Bold**: Set the font weight for the Y-axis coordinates.  <br>- **Italic**: Set the font style to italic for the Y-axis coordinates.   <br>- **Subplot Weight**: Set the size of the space that the subplot occupies in the main chart.     <br>- **Subplot Background Color**: Set the background color of the subplot.       |
| Legend       | Set the style of the legend.  <br>- **Show**: Control the display and hiding of the legend. Default Display.       <br>- **Position**: Set the display position of the legend.                               <br>- **Font**: Set the font, font size, bold, italics, and font color of the legend. |  
| Markers      | Sets whether the markers for maximum and minimum points are displayed on the control. You can set the style, color and size of the markers.    |

**Note:** The historical chart is developed based on Echarts 5.x version. There is a flaw in the graduation number in this version, and it does not take effect according to the set value, causing the historical chart to also have this problem. Please wait for Echarts to fix this defect.


**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example 1**

Use historical chart to show electricity usage.

1. Insert a historical chart on the page.
2. Set the properties of the historical chart.

| **Property** | **Value**   |
|--------------|------|
| Time Range   | Select last 10 minutes.  |
| Query Mode   | Select Raw.    |
| Data         | Bind the tag and select raw value as the sampling type. Set the style of the curve.  <br>![alt text](19.png) Click to set the style. The set attribute values are as follows: <br>![alt text](20.png) <br>- **Tag**: `@Factory:Area`    <br>- **Name**: Electrical energy <br>- **Y Axis**: Y-Axis1           <br>- **Line Color**: #6ec800           <br>-**Line Type**: Line              <br>- **Line Style**: Solid Line        <br>- **Line Width**: 1                <br>- **Area**: heck           <br>- **Alarm Line**: Uncheck           <br>- **Average Line**: Uncheck           <br>- **Symbol Style**: None              <br>- **Symbol Size**: 6                 <br>- **Decimals**: 2     |

3.Click the Preview button to preview.
    ![alt text](21.png)

**Example 2**

Use historical trends to show electricity usage, identifying the maximum and minimum values of electricity on a graph.

1. Insert a historical chart on the page.
2. Set the properties of the historical chart.

| **Property** | **Value**  |
|--------------|---------|
| Time Range   | Select last 10 minutes.   |
| Query Mode   | Select Raw.  |
| Data         | Bind the tag and select raw value as the sampling type. Set the style of the curve. <br>![alt text](22.png)  Click to set the style. The configurations are as follows: ![alt text](23.png) <br>- **Tag**: `@Demo:Totalpower` <br>- **Name**: Totalpower       <br>- **Y Axis**: Y-Axis1          <br>- **Line Color**: #6ec800          <br>- **Line Type**: Line             <br>- **Line Style**: Solid Line       <br>- **Line Width**: 1                <br>- **Area**: Uncheck          <br>- **Alarm Line**: Uncheck          <br>- **Average Line**: Uncheck          <br>- **Symbol Style**: None             <br>- **Symbol Size**: 6                <br>- **Decimals**: 2                |
| Markers      | ![alt text](24.png) |

3.Click the Preview button to preview.
    ![alt text](25.png)