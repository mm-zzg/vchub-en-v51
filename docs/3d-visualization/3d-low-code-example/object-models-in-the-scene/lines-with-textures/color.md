# color

**Description: Modify the color of texture lines**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const tube = await scene.findTube({name:'Tube1'})// Find model
tube.color = '#6ec800'// colour
```
 
**Example:**

Write the above code on the button, click the button to modify the texture line color.

![1](../../../../assets/images/3d_lowcode_object_linetextures_color1.gif)