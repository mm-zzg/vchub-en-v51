# skybox

**Description**: Enter the name of the sky box library created by the user or the system's default sky box library name. If both the background color and background image are set, the sky box should be the main one (the sky box image must be square)

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
view.skyBox='sunset'; //Enter the name of the Sky Box
view.applyChanges(); //Apply Changes (Tips: After setting background related settings, you need to call the applyChanges() method)
```
 
**Example:**

Write the above code on the button, click the button to modify the sky box of the scene.

![1](../../../assets/images/3d_lowcode_SOperation_skybox1.gif)
