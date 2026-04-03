# createLine

**Description**: Create lines to enter the scene

```typescript
const view=await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene=await view. getScene()// Get the scene in the 3D viewer control
const linePaths=[
{x: -20, y: -10, z: 0},
{x: 60, y: 40, z: 0},
{x: 60, y: -10, z: 0},
{x: 60, y: -10, z: 20},
]// Line vertex coordinates
const line=scene.createLine({
name: 'line',//The name of the created line
points: linePaths,//Create vertex coordinates
color: 'rgba(255,255,255)',//The color of the created line
width: 1,//Create the width of the line, default to 1
curve: true,//Whether the created line is a curve, default to false
dashed: true//Whether the created line is a dashed line, default to false
})
```
 
**Example:**

Write the above code on the button, click the button to create a line to the scene

![3d_lowcode_SOperation_createline1](../../../assets/images/3d_lowcode_SOperation_createline1.gif)