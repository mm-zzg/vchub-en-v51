# src

**Description: Modify the link to the embedded page**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const webview = await scene.findWebView({name:'Webview1'})// Find model
webview.src = 'http://localhost:8066/docs/overview/'// Modify the src of embedded pages
```
 
**Example:**

Write the above code on the button, click the button to modify the link of the embedded page. 

![1](../../../../assets/images/3d_lowcode_object_ePage_src1.gif)