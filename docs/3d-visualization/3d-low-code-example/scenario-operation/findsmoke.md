# findSmoke

**Description:** Query the first smoke special effect that meets the criteria in the scene

Search for smoke:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.findSmoke('smoke')//Query the first special effect whose name contains smoke
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the first smoke special effect in the scene with the name including smoke
![1](../../../assets/images/3d_lowcode_SOperation_findsmoke1.gif)

The queried model can use all its methods and properties:
![alt text](3d_lowcode_SOperation_findsmoke2.png)






