# findRain

**Description**: Query the first rain special effect that meets the criteria in the scene

Query Rain:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.findRain('rain')//Query for special effects with names containing rain
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the first rain special effect in the scene whose name includes rain

![1](../../../assets/images/3d_lowcode_SOperation_findrain1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_findrain2.png)



