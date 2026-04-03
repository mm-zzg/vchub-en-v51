








# wireframe

**Description: Does the model enable wireframe mode**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const mesh = await scene.findMesh({ name: 'Forklift' }); // Find model
mesh.wireframe = true; // Does the model have wireframe mode enabled
```
 
**Example:**

Write the above code on the button, click the button to set the model wireframe mode.






![1](../../../../assets/images/3d_lowcode_object_gmodel_wireframe1.gif)