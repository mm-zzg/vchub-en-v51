# canvas

**Description: Modify canvas**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const canvas = await scene.findCanvas({name:'canvas'})// Find model
const canvas2 = document.createElement('canvas')// Create a canvas
const ctx = canvas2.getContext('2d')// 2D rendering canvas
//Set canvas background
ctx.canvas.width = 300;
ctx.canvas.height = 100;
ctx.fillStyle = '#6ec800';
ctx.fillRect(0, 0, 300, 100);
//Draw a brown rectangle with coordinates (0,0) in the upper left corner, a width of 300, and a height of 100
//Set Canvas Text
ctx.font = '20px bold sans serif';
ctx.fillStyle = '#ff0000';
ctx.fillText('New Canvas', 0, 30)// Starting point coordinates 0, 20
canvas.canvas = canvas2// Modify canvas properties
```
 
**Example:**

Write the above code on the button, click the button to modify the canvas. 
![1](../../../../assets/images/3d_lowcode_object_overlays_canvas1.gif)
