# curve

**Description: Modify whether the line is displayed as a curve**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const line = await scene.findLine({name:'Line1'})// Find model
line.curve = false// Is the curve displayed
```
 
**Example:**

Write the above code on the button, click the button, and you can modify whether the line is displayed as a curve.

![1](../../../../assets/images/3d_lowcode_object_line_curve1.gif)

