# createModel

**Description:** Create models from the model library and enter the scene

```typescript
const view=await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3 Viewer1" in the page
const scene=await view.getScene()// Get the scene in the 3D viewer control
scene.createModel({
     path:'models.chariot',  //The address of the model in the model library
     name: 'Forklift',       //The name after creation
     position: { x: 0, y: 0, z: 0 }  //The position after creation
});
```
 
**Example:**

Write the above code on the button, click the button, and the model named "chariot" in the model library will be added to the scene.

![alt text](3d_lowcode_SOperation_createmodel1.png)

![3d_lowcode_SOperation_createmodel2](../../../assets/images/3d_lowcode_SOperation_createmodel2.gif)
