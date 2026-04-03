# createFire

**Description:** Create default flame effects

```typescript
const view = await System.UI.findControl('3DViewer1');  // Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const fire = scene.createFire({
name: 'fire',//Create the name of the flame
position: {x: 0, y: 0, z: 0},//Create the center position of the flame
size: 100//Flame size(default of 5)
});
```
 
**Example:**

Write the above code on the button, click the button, and you can create a flame effect at the specified location

![3d_lowcode_SOperation_createfire1](../../../assets/images/3d_lowcode_SOperation_createfire1.gif)

Modify flame effects and turn off effects: 



![alt text](3d_lowcode_SOperation_createfire2.png)



