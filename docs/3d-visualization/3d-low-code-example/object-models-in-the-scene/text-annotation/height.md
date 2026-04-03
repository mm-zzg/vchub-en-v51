






# height

**Description: Modify text annotation height**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const label = await scene.findTextLabel({name:'Label1'})// Find model
console.log(label.height)// Output text annotation height
await setTimeout(() =>{
  label.height = 3;// Modify text annotation height
  console.log(label.height);// Output text annotation height
},1000)// Set text annotation height and output console after 1 second
```
 
**Example:**

Write the above code on the button, click the button to modify the height of the text annotation.



![1](../../../../assets/images/3d_lowcode_object_textAnnotation_height1.gif)