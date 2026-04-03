# rotateAround

**Description: Camera surround animation**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mesh = await scene.findMesh({name:'chariot'});
scene.camera.rotateAround({
  obj: mesh,//The object surrounded by the camera
  yRotateAngle: 360,//Camera surround angle
  duration: 3000//Camera surround duration ms
});
```
 
**Example:**

Write the above code on the button, click the button to activate the camera surround animation. 

![rotate](../../../assets/images/rotate.gif)

