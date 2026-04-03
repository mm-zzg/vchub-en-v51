# getChildren

**Description: Retrieve the children of the model**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const box = scene.createBasicMesh({
  type: 'Box',//The address of the model in the model library
  name: 'Box2',//The name after creation
  color: '#6ec800',//The color created
  position: {x: 0, y: 0, z: 0},//The created position
  rotation: {x: 0, y: 0, z: 0},//Rotation angle during creation
  size: [30, 30, 30],
});
const box2 = scene.createBasicMesh({
  type: 'Box',//The address of the model in the model library
  name: 'Box222',//The name after creation
  color: '#6ec800',//The color created
  position: {x: 100, y: 100, z: 0},//The created position
  rotation: {x: 0, y: 0, z: 0},//Rotation angle during creation
  size: [30, 30, 30],
  parent: box//Set the parent of the box2 model to box
});
console.log(box.getChildren())// Console output box's child array
```
 
**Example:**

Write the above code on the button, click the button to obtain the child model array of the model. 

![1](../../../../assets/images/3d_lowcode_object_bmodel_getchildren1.gif)
