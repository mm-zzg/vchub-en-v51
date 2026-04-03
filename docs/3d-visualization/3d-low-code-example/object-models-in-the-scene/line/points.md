


# points

**Description: Modify line vertices**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const line = await scene.findLine({name:'Line1'})// Find model
line.points = [{x: 200, y: 200, z: 0}, {x: 100, y: 100, z: 0}, {x: 0, y: 200, z: 200}]// Modify the vertex of a line
```
 
**Example:**

Write the above code on the button, click the button to modify the line vertices.







![1](../../../../assets/images/3d_lowcode_object_line_points1.gif)