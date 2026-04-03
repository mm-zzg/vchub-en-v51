# Page Type

There are 2 page types: page and popup.

There are the following 3 entrances to create pages.

**Entry 1**: The default window of the editor. 

![alt text](1.png)

**Entry 2**: The "Page" menu of the editor.

![alt text](2.png)

**Entry 3**: Right-click any node of "Page" in the "Project" window.

![alt text](3.png)

## **Page**

FFill the entire window with the page.

#### **Page Properties**

![alt text](4.png)

**How to view page properties**

1. Click on a blank area of the page
2. Click on the page’s tab name

    ![alt text](5.png)

3. After zooming the page, click the gray area outside the canvas (the area highlighted in the red box below).

    ![alt text](6.png)

**Page Template**

You can reference a template directly, so that the style of the template can be directly rendered on the current page. After referencing, editing of the template content is not allowed on the current page.

![alt text](7.png)

**Resolution Adaptation**

Different devices (e.g. computers, tablets, mobiles, etc.) have different page sizes and resolutions. If you don't set the appropriate resolution adaptation, the page may be misplaced, overflowed with controls, or incompletely displayed on some devices.

Once resolution adaptation is set up, the system will automatically recognize the resolution of the current device and automatically adapt and adjust it when the page is opened on a device with a different resolution.

VC Hub includes 2 resolution adaptation methods. 

For details,see [Resolution Adaptation](resolution-adaptation.md).

| **Adaptation Method**   | **Description**   |
|-----------|----------|
| ![alt text](8.png) | The aspect ratio remains unchanged.        |
| ![alt text](9.png)| Stretch or zoom the page so that it spreads across the entire window. |

**Custom Properties**

In addition to the basic property settings, you can create custom properties for the page. You can use custom properties like any other property, such as data binding, scripts, and styles.

Custom properties are important for passing parameters from one page to another. 

For details,see [Page Parameter Passing](page-parameter-passing.md).

To configure custom properties, do the following:

1. Click on an empty space on the page.
2. Click Appearance >Page  Custom Property.
3. Click the plus icon to add a row.
4. Enter the custom property name, data type, and initial value.
5. The custom property is automatically saved after you add it. 

![alt text](10.png)

## **Popup Page**

A window that appears above the page. On the running page, the popup window can be dragged to change its position. However, you can only drag the popup page within the current window, not outside the window.

#### **Popup Page Properties**

A popup page has more properties than a page, such as title bar settings. You can set the title bar style of the popup page in the Appearance property of the popup page according to your specific needs.

![alt text](11.png)

**How to view popup page properties**

1. Click on a blank area of the page
2. Click on the page’s tab name

    ![alt text](12.png)

3. Click the gray area outside the canvas

    ![alt text](13.png)

#### **Popup Position**

You can specify a specific location to open the popup page. 

For details,see [Navigation](navigation.md).

![alt text](14.png)

Example of a popup window style:  

![alt text](15.png)

![alt text](16.png)



