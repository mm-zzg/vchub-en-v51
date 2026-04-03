# createPlane

**Description**: Creating Plane

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
scene.createPlane({
  name: 'Plane',//The name of the created surface
  position: {x: 10, y: 0, z: 0},//Create position
  image: 'a.Arrow.png',//Create a texture for the face; (Default none) You can use the map path or URL from the model library; Recommended image formats: JPG, PNG, JPEG;
  doubleSide: true,//Whether the side is displayed on both sides (default no). Note that dragging the mouse to check for a single side is necessary
  color: '#6ec800',//The color of the created face (default gray white)
  rotation: {x: 0, y: 0, z: 0},//The rotation angle of the created face
  size: [20,11],//Initial length and width of the created face, default to 12, 12
  repeatX: 15,//The number of times the image is repeated in the x-direction (default 1)
  repeatY: 6////The number of times the image is repeated in the y-direction (default 1)
})
```
 
**Example:**

Write the above code on the button, click the button to create a plane to the scene

![3d_lowcode_SOperation_createplane1](../../../assets/images/3d_lowcode_SOperation_createplane1.gif)









