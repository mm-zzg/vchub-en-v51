# createTube

**Description**: Create curves that can be mapped

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const linePaths=[
{x: -20, y: -10, z: 0},
{x: 60, y: 40, z: 0},
{x: 60, y: -10, z: 0},
{x: 60, y: -10, z: 20},
]// Line vertex coordinates
const tube = scene.createTube({
name: 'tube',//Create a line name
points: linePaths,//Create line vertex coordinates
color: 'rgba(189,16,224)',//Create line colors
width: 3,//Create line width (default 1)
image: 'a.Arrow.png',//Create a line map path
repeatX: 15,//The number of times the image is repeated in the x-direction (default 1)
repeatY: 6////The number of times the image is repeated in the y-direction (default 1)
})
```
 
**Example:**

Write the above code on the button, click the button, and you can create a curve for the texture to the scene

![3d_lowcode_SOperation_createtextlabel1](../../../assets/images/3d_lowcode_SOperation_createtube1.gif)
