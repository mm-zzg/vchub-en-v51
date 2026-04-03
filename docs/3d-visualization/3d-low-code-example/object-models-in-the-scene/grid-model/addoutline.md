# addOutline

**Description: Set model outline**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const mesh = await scene.findMesh({ name: 'Forklift' });
mesh.addOutline({
    color: 'red',
    edgeStrength: 3,
    edgeGlow: 1,
    pulsePeriod: 5
})
```
 
**Example:**

Write the above code on the button, click the button to set the model outline.










![1](../../../../assets/images/3d_lowcode_object_gmodel_addoutline1.gif)