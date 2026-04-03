# queryFire

**Description:** Query all fire special effects that meet the conditions in the scene

Query fire:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.queryFire('fire')//Query special effects with names containing fire
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the fire special effects in the scene whose name includes fire

![1](../../../assets/images/3d_lowcode_SOperation_queryfire1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_queryfire2.png)




