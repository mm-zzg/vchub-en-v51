








# removeOutline

**Description: The model closes the edge check**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const mesh = await scene.findMesh({ name: 'Forklift' });
mesh.removeOutline();
```
 
**Example:**

Write the above code on the button, click the button to remove the model outline.



![1](../../../../assets/images/3d_lowcode_object_gmodel_removeoutline1.gif)