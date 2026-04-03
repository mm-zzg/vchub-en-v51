# queryCanvas

**Description**: Query all image annotations that meet the conditions in the scene

Query image annotations:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.queryCanvas ({
  //Id: "3b013f32-d6b0-484e-835c-e63e75d30ecb",//To query the unique uuid of the model
  name: 'canvas',//Blurred query name includes image annotations for canvas
  //User defined data content for userData
})
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the models in the scene with names containing canvas, including groups

![1](../../../assets/images/3d_lowcode_SOperation_querycanvas1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_querycanvas2.png)



