# Pie Chart

A pie chart is used to display the proportion of different categories or components within a whole. It is based on a circle, which is divided into several sectors, with each sector's angle corresponding to the proportion of the category or component it represents. Pie charts are particularly suitable for showing percentages and other data relationships relative to the total.

There are two styles: **Pie Chart** and **Ring Chart**.

![alt text](36.png)

**Properties**

| **Name**          | **Description**    |
|-------------------|------------------|
| Name              | The name of this control. |
| X                 | The distance between the left side of the control and the left side of the canvas, in pixels. |
| Y                 | The distance between the top of the control and the top of the canvas, in pixels.  |
| W                 | The width of the control, in pixels.  |
| H                 | The height of the control, in pixels.  |
| Data              | Click the dataset button to set default data for the pie chart, and click the binding button to bind variables, properties, or write expressions for the cells in the dataset. |
| Refresh Frequency | The data on the pie chart is refreshed at this frequency.   |
| Style             | Set the display style of the pie chart. Contains pie and ring charts.  |
| Background        | The overall background color of the control.   |
| Border            | The border color of each slice of the pie chart.   |
| Border thickness  | The border thickness of each slice of the pie chart.   |
| Section Colors    | Set the colors for different segments of the pie chart, with the default being the colors shown on the color palette.   |
| Margin            | Set the distance from the center of the pie chart to its selection box, typically used to define the size of the pie chart. When the control style is set to a ring chart, both inner and outer radius need to be specified.  |
| Legend            | Sets the style for the pie chart legend.   <br>- **Show**: Control the display and hiding of the legend. Default Display.   <br>- **Position**: Set the display position of the legend.                               <br>- **Font**: Set the font, font size, bold, italics, and font color of the legend.    |
| Label             | Set the name and value of the dataset, and perform variable binding in the cell binding window.  <br>- **Show**: Control the display and hiding of label values. Hidden by default.   <br>- **Position**: Set the display position of the label value.       <br>- **Numeric typ**: Set the data type for the value displayed in the annotation. It can be either the value or the percentage. <br>- **Decimals**: The number of decimal places displayed for label values.Can be a value or a percentage.                 <br>- **Font**: Set the font, font size, bold, italics, and font color of the legend.   |

**Event**

Allows you to perform specific events based on certain conditions. See the full description of each event on the [Event](../../event/index.md) page.

**Example**

Use a pie chart to display the daily production capacity share of different production lines.

1. Insert a pie chart on the page.
2. Set the properties of the pie chart.

| **Property** | **Value**              |
|--------------|-------------------------------------------------|
| Legend       | Display, Microsoft YaHei, font size 14.    |
| Label        | - **Show**: Turn on     <br>- **Position**: Outside.     <br>- **Numeric type**: Percentage.  <br>- **Decimals**: 1.          <br>- **Font**: Calibri, 14. |
| Data         | Click the **Dataset** button to configure the dataset. <br>![alt text](37.png) <br>![alt text](38.png)  <br>After completing the setup, click the **Bind** button to perform dynamic cell binding.  ![alt text](39.png) |

3.Click the Preview button to preview.<br>
    ![alt text](40.png)

4.Exit preview mode, change the pie chart style to a donut chart on the design page, disable the legend display, and then preview again.<br>
    ![alt text](41.png)