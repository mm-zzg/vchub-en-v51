# findTube

**Description**: Query the first texture curve that meets the criteria in the scene

Query texture curves:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.findTube({
  //Id: "3b013f32-d6b0-484e-835c-e63e75d30ecb",//To query the unique uuid of the model
  name: 'tube',//Fuzzy query name includes image annotation of the tube
  //User defined data content for userData
})
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the first matching model in the scene whose name includes the tube

![1](../../../assets/images/3d_lowcode_SOperation_findtube1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_findtube2.png)





