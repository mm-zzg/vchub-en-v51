# Real Time Alarm

The real time alarm control shows the on going alarms, including alarms for the current node and alarms for remote nodes in a networked environment. 

The system memory supports up to 50,000 alarm records. Any excess records will be removed starting from the earliest ones, with cleanup performed every minute.

By default, all alarm information is displayed, and the control only supports displaying the latest 2,000 alarm data. You can also set filters.

Support operations such as acknowledging, shelving, and filtering for all alarms displayed in the list.

![alt text](1.png)


**Interface Elements**

![alt text](2.png)

You can set the columns to be displayed by clicking the "Column Setting" button on the preview and running page. Click and drag the margin of the column to adjust its width. You can also sort columns in ascending or descending order by clicking the up or down arrow next to each column header.

**Properties**

| **Name**                 | **Description**   |
|--------------------------|--------------------|
| Name                     | The name of this control.  |
| X                        | The distance from the left side of the control from the left side of the canvas.  |
| Y                        | The distance from the top of the control from the top of the canvas.  |
| W                        | The width of the control.  |
| H                        | The height of the control.  |
| Show                     | Set which buttons are displayed on the control. |
| Priority Color           | Set the color and flashing effect for each alarm level.  |
| Border Color             | Set the table line color of the outer border and table body of the control.  |
| Border Thickness         | Set the thickness of the table line of the outer border of the control and the table body.    |
| Header                   | Set the background color, font type, font size, bold, italic, and font color of the header.  |
| Body                     | Set the background color, font type, font size, bold, italic, and font color of the body.   |
| Tab                      | Set the style of active and shelved tabs.   <br>- **Indicator bar**: After selecting the tab, the color of the indicator bar displayed below the tab.   <br>- **Active**: Set the background color, border color, font type, font size, bold, italic, font color for active tab.  <br>- **Shelved**: Set the background color, border color, font type, font size, bold, italic, font color for shelved tab. | |
| Alarm Sound              | Set the alarm sound.  <br>- **Enable**: Used to turn the alarm sound on or off.  <br>- **Sound**: With a built-in beep, users can also manually upload alarm sounds, and up to 5 can be uploaded. <br>- **Critical**: Set the alarm sound of the alarm priority of "Critical".                                <br>- **High**: Set the alarm sound of the alarm priority of "High".                                <br>- **Medium**: Set the alarm sound of the alarm priority of "Medium".                                        <br>- **Low**: Set the alarm sound of the alarm priority of "Low".  |
| Filter Panel             | Set the style of the filter panel. <br>- **Background**: Background color of the filter panel. <br>- **Title Font**: Set the font type, font size, bold, italic, and font color of the panel name.  <br>- **Tag**: After the filter panel is expanded, the style of the tab displayed.  <br>![alt text](3.png) <br>Including the background color, border color, font type, font size, bold, italic, font color displayed when the tab is selected and not selected. | 
| Button Style             | Set the style of the buttons used on the control. Click the button style settings button to set it up.  <br>![alt text](4.png) Sound Button.Set the color of the sound button.    <br>![alt text](5.png) Setting Button.Set the color of the setting button.        <br>![alt text](6.png) Reset Button.Set the color of the reset button.    <br>![alt text](7.png) Filter Button.Set the color of the filter button.    <br> ![alt text](8.png) Search box.Set the background color, border color of the search box, and the font type, font size, bold, italic, and font color of the search box. <br>![alt text](9.png) Acknowledge Button.Set the background color, border color, font type, font size, bold, italic, font color of the acknowledge button.         <br>![alt text](10.png) Shelve Button: Set the background color, border color, font type, font size, bold, italic, font color of the shelve button.  <br>![alt text](29.png) Unshelve Button: Set the background color, border color, font type, font size, bold, italic, font color of the unshelve button.                      | 
| Filter                   | Check the required filter criteria.  |
| Column                   | Set the column  that need to be displayed in the active tab and shelved tab.  |
| Action                   | Set the operation button and set the trigger operation to be executed when the alarm is triggered.  |
| Maximum Number of Alarms | Set the maximum number of alarms allowed by the control to display.|

**Event**

Allows you to perform a specific event based on certain conditions. See the full description of each event on the [Event](../../../event/index.md) page. 

**Example 1**

In the designer, you can configure the background color to other colors. In this example, set the color of the Medium alarm to green.

![alt text](30.png)

**Example 2**

On the running page, set the filter criteria in the filter button to filter only the alarm data with high alarm type.

![alt text](31.png)

**Example 3**

No buttons are displayed, only alarm information is displayed. In the "Appearance Display" of the property, all options are not selected.

![alt text](32.png)

The display effect is as follows:

![alt text](33.png)



