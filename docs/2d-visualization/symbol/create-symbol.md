# Create Symbol

You can create symbols in the "Symbol" editor. Once created, a symbol can be used as a template and then instantiated multiple times across different screens. Each instance will have the same components and properties, but the data can vary. Any changes made to the template will automatically update across all symbol instances.

## Add Symbol

You can expand any symbol library, click the ➕ within the library, and a new window will pop up. Set the name of the symbol and click the "OK" button to create the symbol.

![alt text](9.png)

After creation, an empty symbol editor will be displayed in the main design space. The initial symbol editor is completely transparent. You can set a background if you want.

![alt text](10.png)

**Properties**

![alt text](11.png)

| **Name**        | **Description**   |
|-----------------|-----------|
| W               | Width of the symbol. |
| H               | Height of the symbol.   |
| Background      | Background color of the symbol, supports property binding  <br>![alt text](12.png) |
| Custom Property | You can use custom properties like any other properties, such as for data binding, scripts, and styles. To configure custom properties, follow these steps:  <br>1. Click on the blank area of the symbol editor. <br>2. Go to "Appearance" > "Custom Property." <br>3. Click the plus (+) icon to add a row. <br>4. Enter the custom property name, data type, and initial value. <br>5. The custom property is automatically saved after you add it.  <br> ![alt text](13.png)|

**Note:** Symbols support nesting, allowing one symbol to be embedded within another. However, a symbol cannot be nested within itself.

**How to view the properties of the Symbol Editor window**

1. Click on a blank area of the symbol editor
2. Click on its tab name

    ![alt text](14.png)

3. click the gray area outside the canvas (the area highlighted in the red box below).

    ![alt text](15.png)

## Edit Symbol

Just like drawing a screen, you can add components (e.g., controls, images, symbols) in the symbol window. Once a symbol is modified, all instances of that symbol will be updated.

When your symbol creation is complete, you can open the symbol for editing using the following four methods:

- **Method 1:** Double-click the symbol in the "Symbol Library" to automatically open the symbol's editing window in the editor.
- **Method 2:** Right-click the symbol and select "Edit" from the context menu that appears.

    ![alt text](16.png)

- **Method 3:** In the editor, double-click the symbol component to open the symbol for editing.
- **Method 4:** In the editor, right-click the selected symbol component and choose the "Edit" button from the context menu to open the symbol.

    ![alt text](17.png)

## Save As Symbol

After creating the symbol, click the "Save As" button in the Page menu. Set the desired symbol library and symbol name to complete the creation.

![alt text](18.png)

## Move Symbol

You can change the symbol's associated symbol library by dragging and dropping. To move a symbol to another library, click on the symbol and drag the mouse to the target library, then release the mouse to drop it.

![symbol](../../assets/images/symbol.gif)

**Note:** If the symbol is currently open, you cannot perform the operation of moving the symbol. 

## Copy/Paste Symbol

Right-click on a symbol in the symbol library and select the "Copy" option to duplicate the symbol.

![alt text](19.png)

After copying, click the "..." in the symbol library to paste the symbol.

![alt text](20.png)

## Instance Symbol

Once the symbol is created, you can drag the symbol onto the screen or screen template to create multiple instances of the symbol. After the instances are created, you can manipulate their properties just like any other control.

![alt text](21.png)

**Properties of the Symbol Instance**

| **Name**        | **Description**                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------|
| Name            | Name of this symbol instance.                                                                                                    |
| X               | The distance from the left side of the canvas to the left side of the symbol instance.                                           |
| Y               | The distance from the top of the canvas to the top of the symbol instance.                                                       |
| W               | The width of the symbol instance.                                                                                                |
| H               | The height of the symbol instance.                                                                                               |
| Path            | The complete path of the symbol instance.                                                                                        |
| Custom Property | These are consistent with the custom properties set for the symbol. You can click the bind button to configure the property binding. |