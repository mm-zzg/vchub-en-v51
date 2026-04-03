# querySnow

**Description**: Query all eligible snow effects in the scene

Query Snow:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.querySnow('snow')//Query special effects with a name containing’snow’
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can search for snow effects in the scene with names containing Snow

![1](../../../assets/images/3d_lowcode_SOperation_querysnow1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_querysnow2.png)


