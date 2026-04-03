







# fontSize

**Description: Modify text annotation size**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const label = await scene.findTextLabel({name:'Label1'})// Find model
label.fontSize = 100// Modify text annotation size
```
 
**Example:**

Write the above code on the button, click the button to modify the size of the text annotation.




![1](../../../../assets/images/3d_lowcode_object_textAnnotation_fontsize1.gif)