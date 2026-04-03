# findSnow

**Description:** Query the first snow effect that meets the criteria in the scene

Query Snow:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.findSnow('snow')//Query for special effects where the name contains’snow'
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the first snow effect in the scene with the name containing Snow

![1](../../../assets/images/3d_lowcode_SOperation_findsnow1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_findsnow2.png)


