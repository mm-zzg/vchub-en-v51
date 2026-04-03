# size

**Description: Modify the size of canvas**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const canvas = await scene.findCanvas({name:'Canvas'})// Find model
canvas.size = {width: 1000, height: 1000}// Modify the size of canvas
```
 
**Example:**

Write the above code on the button, click the button to modify the size of the canvas. 

![1](../../../../assets/images/3d_lowcode_object_overlays_size1.gif)
