# image

**Description: Modify face images**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const plane = await scene.findPlane({name:'Plane1'})// Find model
plane.image = 'a.win10.jpg'// Modify image
```
 
**Example:**

Write the above code on the button, click the button to modify the image.

![1](../../../../assets/images/3d_lowcode_object_surface_image1.gif)

