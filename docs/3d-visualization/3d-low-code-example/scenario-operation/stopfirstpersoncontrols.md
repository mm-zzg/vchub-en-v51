# stopFirstPersonControls

**Description:** Turn off first person mode

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
scene.stopFirstPersonControls()// Turn off first person mode
```
 
**Example:**

Write the above code on the button, click the button, and turn off the already enabled first person mode.

![1](../../../assets/images/3d_lowcode_SOperation_stopfirstpersoncontrols1.gif)


