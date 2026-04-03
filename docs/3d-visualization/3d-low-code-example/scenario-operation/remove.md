# remove

**Description**: **Delete model**

Query the model and delete it:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const chariot = await scene.query({
  name: 'chariot',
})// Fuzzy query for models with chariot names, returning an array
chariot.forEach((ele) =>scene.remove(ele))// Traverse the array and perform a delete all operation

```
 
**Example:**

Write the above code on the button, click on the button, and delete all models with names containing charts

![1](../../../assets/images/3d_lowcode_SOperation_remove1.gif)

3D scene model:

![alt text](3d_lowcode_SOperation_remove2.png)
