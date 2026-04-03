# flyPath

**Description: Camera surround animation**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
await scene.camera.flyPath({
  paths: [{x: 110, y: 150, z: -50}, {x: 92, y: 120, z: -36}, {x: 23, y: 25, z: 11}, {x: -30, y: 10, z: 27}],//Camera flight path
  duration: 1800,//Camera surround duration ms
  target: [0,0, -27]//The coordinate of the camera's orientation during flight(default orientation is the current orientation)
});
```
 
**Example:**

Write the above code on the button, click the button to start the camera flying animation 

![flypath](../../../assets/images/flypath.gif)

