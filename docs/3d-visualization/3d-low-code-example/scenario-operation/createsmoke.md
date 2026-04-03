# createSmoke

**Description**: Create default smoke effects

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const smoke = scene.createSmoke({
  name: 'smoke',//Create the name of the smoke
  position: {x: 0, y: 0, z: 0},//Create the center position of the smoke
  size: 5//Smoke size(default 1)
});
```
 
**Example:**

Write the above code on the button, click the button, and you can create a smoke effect at the specified location

![3d_lowcode_SOperation_createsmoke1](../../../assets/images/3d_lowcode_SOperation_createsmoke1.gif)

Turn off special effects:


![alt text](3d_lowcode_SOperation_createsmoke2.png)


