# createSnow

**Description**: Create default snow effects

```typescript
const view=await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene=await view.getScene();
scene. createSnow({
name: 'snow',//Create the name of the snow
position: {x: 0, y: 0, z: 0},//Create the center position for snowfall
range: {depth: 1000, width: 500, height: 500},//The default range for snowflake falling is (1000500500). The depth value is the range of depth/2 on the y-axis up and depth/2 on the y-axis down
speed: 1,//falling speed (default 0.5)
count: 2500//Number of snowflakes (default to 2000)
});
```
 
**Example:**

Write the above code on the button, click the button, and you can create a snow effect at the specified location

![3d_lowcode_SOperation_createsmoke1](../../../assets/images/3d_lowcode_SOperation_createsnow1.gif)

 Modify snow effects and turnoff effects:

![alt text](3d_lowcode_SOperation_createsnow2.png)





  

