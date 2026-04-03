# createTextLabel

**Description**: Create a text annotation at a specified location (using the default text font does not support modification)

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
scene.createTextLabel({
  name: 'text1',//Create the name of the face text annotation
  text: 'Hello World!',// The content of text annotations
  fontSize: 16,//Font size (default 16)
  fontColor: '#6ec800',//Font color (default gray white)
  height: 1,//Text height (default 1)
  position: {x: 0, y: 10, z: 0},//Create the position of the text
  rotation: {x: 0, y: 10, z: 0},//Create the rotation angle of the text
  scale: {x: 1, y: 1, z: 1},//Create initial scaling of text
})
```
 
**Example:**

Write the above code on the button, click the button, and you can create a text annotation at the specified position

![3d_lowcode_SOperation_createtextlabel1](../../../assets/images/3d_lowcode_SOperation_createtextlabel1.gif)


