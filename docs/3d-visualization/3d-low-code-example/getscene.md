# getScene

**Description**: Retrieve the 3D scene from the 3D viewer, and the obtained return value can be obtained using all methods in scene operations

```typescript
const view = await System.UI.findControl('3DViewer1'); // Obtain a 3D Viewer control named "3DViewer1" in the page
const scene =await view.getScene(); // Get the scene in the 3D viewer control
```
 
![alt text](3d_3dlowcode_getscene1.png)

