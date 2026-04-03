

# rotation

**Description: Changing the model rotation angle**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const box = await scene.findMesh({name:'Box2'})// Find model
box.rotation = {x: 45, y: 45, z: 45}// Modify model rotation angle
```
 
**Example:**

Write the above code on the button, click the button to modify the model rotation angle.





![1](../../../../assets/images/3d_lowcode_object_gmodel_rotation1.gif)