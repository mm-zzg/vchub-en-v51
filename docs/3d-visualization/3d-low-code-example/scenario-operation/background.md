# background

Description: Set 3D scene background color

```typescript
const view = await System.UI.findControl('3DViewer1');  // Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene(); // Get the scene in the 3D viewer control
view.backgroundColor= '#6ec800';  // Change the background color to green
view.applyChanges(); // apply
```
 
Example:

Write the above code on the button, click the button to modify the background color of the scene.

![3d_lowcode_SOperation_background1](../../../assets/images/3d_lowcode_SOperation_background1.gif)
