


# text

**Description: Modify the text content of text annotations**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const label = await scene.findTextLabel({name:'Label1'})// Find model
label.text = 'Label Changed'// Modifying Text Annotation Content
```
 
**Example:**

Write the above code on the button, click the button to modify the image. 


![1](../../../../assets/images/3d_lowcode_object_textAnnotation_text1.gif)