# color

**Description: Modify line color**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const line = await scene.findLine({name:'Line1'})// Find model
line.color = '#12b5ac'// Change the color of lines
```
 
**Example:**

Write the above code on the button, click the button to modify the line color.

![1](../../../../assets/images/3d_lowcode_object_line_color1.gif)



