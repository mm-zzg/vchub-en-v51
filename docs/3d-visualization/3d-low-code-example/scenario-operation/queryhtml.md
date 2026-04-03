# queryHtml

**Description**: Query all Html that meet the conditions in the scene

Query HTML:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.queryHtml({
  //Id: "3b013f32-d6b0-484e-835c-e63e75d30ecb",//To query the unique uuid of the model
  name: 'HTML',//Fuzzy query for models with names containing HTML
  //User defined data content for userData
})
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the models in the scene with names containing HTML, including groups

![1](../../../assets/images/3d_lowcode_SOperation_queryhtml1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_queryhtml2.png)



