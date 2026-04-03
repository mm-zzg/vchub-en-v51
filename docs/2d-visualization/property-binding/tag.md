# Tag

Tag binding is to bind a property directly to a tag property, usually the tag value, but also other properties of the tag. Each time a property of the selected tag changes, the new value is pushed to the bound property. If you select a tag rather than a specific property of that tag, then it is considered to bind to the 'value' property of the tag.

## Binding

**Example 1**

Display the value of the tag on the LED Display  in real time.

1. Draw a LED Display on the page.
2. Set the fill color of the LED Display to 6ec800 and the font color to ffffff.
3. Click the "Text" binding button.
4. After selecting the tag in the properties pop-up window, click the OK button to complete the binding.

    ![alt text](9.png)

    ![alt text](10.png)

**Example 2**

Capacity values are displayed in real time on a pie chart.

1. Draw a realtime chart on the page.
2. Click the "Data" binding button.
3. Click the "Select Tags" button to select tags.

    ![alt text](11.png)

4. Set the appearance of each line.

    ![alt text](12.png)

    ![alt text](13.png)

**Example 3**

Displays the tag's quality code within a label.

1. Draw a label on the page.
2. Click the "Text" binding button.

    ![alt text](14.png)

3. Bind the alarm property of the tag to check whether the tag is currently alarming, true means alarming.

    ![alt text](15.png)



 

