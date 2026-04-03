# position

**Description: Set the position of the camera**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
scene.camera.position = {x: 30, y: 17, z: -10}// Set camera positions to 30, 17, -10
```
 
**Example:**

Write the above code on the button, click the button to set the position of the camera

![position](../../../assets/images/position.gif)

