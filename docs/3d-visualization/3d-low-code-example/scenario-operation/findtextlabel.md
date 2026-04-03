# findTextLabel

**Description:** Query the first text annotation that meets the criteria in the scene

Query text annotations:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.findTextLabel({
  //Id: "3b013f32-d6b0-484e-835c-e63e75d30ecb",//To query the unique uuid of the model
  name: 'text',//Fuzzy query for text annotations with names containing text
  //User defined data content for userData
})
console.log(mash)//Output all queried results
```
 
**Example:**

Write the above code on the button, click the button, and you can query the first text annotation in the scene where the name contains text

![1](../../../assets/images/3d_lowcode_SOperation_findtextlabell.gif)
The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_findtextlabel2.png)





