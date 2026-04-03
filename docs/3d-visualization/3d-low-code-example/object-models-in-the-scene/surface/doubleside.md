# doubleSide

**Description: Whether the modified surface is displayed on both sides**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const plane = await scene.findPlane({name:'Plane1'})// Find model
plane.doubleSide = true// Set up double-sided display
```
 
**Example:**

Write the above code on the button, click the button to set double-sided display.

![1](../../../../assets/images/3d_lowcode_object_surface_doubleside1.gif)

