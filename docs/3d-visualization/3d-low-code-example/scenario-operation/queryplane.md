# queryPlane

**Description:** Query all faces that meet the conditions in the scene

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.queryPlane({
    //id:"3b013f32-d6b0-484e-835c-e63e75d30ecb", //the uuid of the model
    name: 'Plane', //Fuzzy query for faces whose names contain Plane
    //userData  User-defined data content
})
console.log(mash) //Output all the results of the query
```
 
**Example:**

Write the above code on the button, click the button, and you can query the models and groups in the scene whose names include Plane
![1](../../../assets/images/3d_lowcode_SOperation_queryplane1.gif)

The queried model can use all its methods and properties:

![alt text](3d_lowcode_SOperation_queryplane2.png)







