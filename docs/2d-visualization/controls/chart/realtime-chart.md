# Real Time Chart

A real time chart is a chart used to display real time changes in data over time. The X-axis is the time axis and the Y-axis is the data axis.

![alt text](1.png)

**Properties**

| **Name**          | **Description**   |
|-------------------|-------------------|
| Name              | The name of this control.  |
| X                 | The distance between the left side of the control and the left side of the canvas, in pixels.      |
| Y                 | The distance between the top of the control and the top of the canvas, in pixels.  |
| W                 | The width of the control, in pixels.   |
| H                 | The height of the control, in pixels.    |
| Data              | Click the Bind button to bind data to the control. Double-click the tag in the Select Tag window to bind it. After binding the tag, click the Set button to set the curve style.  <br>![alt text](2.png)  Clicking this button allows you to set the data source and style of the curve. <br>![alt text](3.png) <br>- **Tag**: Set the data source for the curve.  You can copy the path of a tag directly to the "Name” column by clicking on the following symbol on the far right of the "Tag" column. <br>![alt text](4.png)   <br>- **Name**: Set the name of the curve.  <br>- **Y Axis**：Select a Y-axis as the Y-axis of the current tag. <br>- **Line Color**: Set the color of the curve.<br>- **Line Type**：The type of the curve.   <br>- **Line Style**: The style of the curve.   <br>- **Line Width**: The width of the curve.  <br>- **Area**: Set the background color of the area between the curve and the axis.  <br>- **Alarm Line**: Set whether the alarm value of the tag is displayed as a line on the current control.  Click the Set button of the alarm line to select the alarm line to be displayed and set the style for it.   Check the checkbox of the alarm line to enable the display of the alarm line on the control. <br>- **Symbol Style**: Set the style of markers on the curve. <br>- **Symbol Size**: The size of the mark.   <br>- **Decimals**: Move the mouse to the number of decimal places displayed on the curve.  | |
| Refresh Frequency | Data on the control is refreshed at this frequency.  |
| Show              | Select Tag Button: Set the display and hiding of the tag selection button.When visible, this button on the running page allows users to reconfigure the tags and their corresponding curve display styles. |
| Button Style      |  Select Tag Button: Set the color of the tag selection button.  |
| Color             | Set the color effect of the control.  <br>- **Background**: The overall background color of the control. <br>- **Grid**: The line color of the grid. <br>- **X Axis**: The axis color of the X Axis.                |    |
| Margin            | Set the spacing between the control and its selection box. Ensure that the chart is displayed clearly and sufficient space is reserved for chart elements, such as time or legend.    |
| X Axis            | Set the style of the X Axis.  <br>- **Show Grid**: ontrol the display and hiding of the grid.  <br>- **Time Format**: Set the format of the time displayed on the X-axis, you can choose the time format preset by the system or input it manually, the time format set must meet the time format requirements of Echarts.  For details, see  [https://echarts.apache.org/zh/option.html#xAxis.axisLabel.formatter](https://echarts.apache.org/zh/option.html#xAxis.axisLabel.formatter) <br>- **Time Range(s)**: The time range shown on the x-axis.  <br>- **Font**: Set the font, font size, bold, italics, and font color of the text displayed on the X-axis.   |
| Y Axis            | Set the style of the Y-axis.  <br>- **Show Grid**: Control the display and hiding of the grid. <br>- **Enable Subplot**: Control whether embedding another chart is allowed in the main chart. <br>- **Grid(s)**: Set the number of dividing lines inserted on the Y-axis. <br>- **Axes**: Display the number of rows and columns of the axis.     <br>![alt text](5.png) Clicking this button allows you to set the style of the axis.  <br> ![alt text](6.png) <br>- **Name**: The name of the Y axis. <br>- **Auto Range**: The range of the Y-axis changes dynamically according to the range of values. If checked, the value range of the Y-axis will be automatically determined. If unchecked, the min and max values will be used.  When Auto is selected, the min and max values become invalid. <br>- **Min**: Minimum value of Y axis.  <br>- **Max**: The maximum value of the Y-axis.  <br>- **Decimals**: Set the number of decimal places displayed on the Y-axis tick values. <br>- **Show**: Control the display and hiding of the Y-axis.  <br>- **Position**: Set the display position of the Y-axis.  <br>- **Offset(px)**: Set the offset of the Y-axis relative to its default position.<br>- **Axis Color**: Set the color of the Y-axis. <br>- **Font**: Set the font for the Y-axis labels.<br>- **Font Size**: Set the font size for the Y-axis coordinates. <br>- **Font Color**: Set the font color for the Y-axis coordinates.<br>- **Bold**: Set the font weight for the Y-axis coordinates. <br>- **Italic**: Set the font style to italic for the Y-axis coordinates. <br>- **Subplot Weight**: Set the size of the space that the subplot occupies in the main chart.  <br>- **Subplot Background Color**: Set the background color of the subplot. | 
| Legend            | Set the style of the legend. <br>- **Show**: Control the display and hiding of the legend. Default Display.  <br>- **Position**: Set the display position of the legend.     <br>- **Font**: Set the font, font size, bold, italics, and font color of the legend. |

**Note:** The real time chart is developed based on Echarts 5.x version. There is a flaw in the graduation number in this version, and it does not take effect according to the set value, causing the real time chart to also have this problem. Please wait for Echarts to fix this defect.

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example 1**

Use real time chart to display water temperature.

1. Insert a real time chart on the page.
2. Set the properties of the real time chart.

| **Property** | **Value**  |
|--------------|---------------------|
| X Axis       | Turn off the display of the grid. |
| Y Axis       | Turn off the display of the grid.  |
| Data         | Bind tags and set the style of the curve.  ![alt text](7.png) <br>- **Tag**: `@Demo:temperature` <br>- **Name**: Water Temperature <br>- **Y Axis**: Y-Axis1     <br>- **Line Color**: #6ec800           <br>- **Line Type**: Line              <br>- **Line Style**: Solid line        <br>- **Line Width**: 1                 <br>- **Area**: Uncheck           <br>- **Alarm Line**: Uncheck           <br>- **Symbol Style**: None              <br>- **Symbol Size**: 6              <br>- **Decimals**: 2           |

3.Click the Preview button to preview.<br>
    ![alt text](8.png)

**Example 2**

Use real time chart to display water temperature, and display the water temperature alarm line.

1. Insert a real time chart on the page.
2. Set the properties of the real time chart.

| **Property** | **Value**   |
|--------------|-------------|
| X Axis       | Turn off the display of the grid.  |
| Y Axis       | Turn off the display of the grid. |
| Data         | Bind tags and set the style of the curve. <br>![alt text](9.png)<br>- **Tag**: `@Demo:temperature`  <br>- **Name**: temperature   <br>- **Y Axis**: Y-Axis1  <br>- **Line Color**: #6ec800  <br>- **Line Type**: Line  <br>- **Line Style**: Solid line  <br>- **Line Width**: 1    <br>- **Area**: False  <br>- **Alarm Line**: Checked. Select High Temperature Alarm, set Line Color to Red and Style to Dashed.  <br>![alt text](10.png)   <br>- **Symbol Style**: None    <br>- **Symbol Size**: 6    <br>- **Decimals**:2  |

3.Click on the preview button to preview. The red dotted line is the alarm line for the water temperature. The alarm line allows you to determine only at which moment the tag generates an alarm.<br>
    ![alt text](11.png)



