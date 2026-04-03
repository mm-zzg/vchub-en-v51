







# opacity

**Description: Changing model transparency**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const box = await scene.findMesh({name:'Box2'})// Find model
box.opacity = 0.25// Modify model transparency (0-1)
```
 
**Example:**

Write the above code on the button, click the button to modify the model transparency.





![1](../../../../assets/images/3d_lowcode_object_gmodel_opacity1.gif)