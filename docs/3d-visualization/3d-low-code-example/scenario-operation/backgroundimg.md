# backgroundImg

**Description**: Set background image

```typescript
const view = await System.UI.findControl('3DViewer1');  // Obtain a 3D viewer control named "3DViewer1" in the page
view.backgroundImage='a.win10.jpg'; // Set the background image to a Win10.jpg image in Library A
view.applyChanges(); // Application Tips: After setting the background related settings, you need to call the applyChanges() method
```
 
**Example**:

Write the above code on the button, click the button to modify the background image of the scene.

![3d_lowcode_SOperation_backgroundimg1](../../../assets/images/3d_lowcode_SOperation_backgroundimg1.gif)
