



# rotateTo

**Description: Model rotation animation**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const mesh = await scene.findMesh({ name: 'Forklift' });
const meshRotation = mesh.rotation;
mesh.rotateTo({
    rotation: { x: meshRotation.x, y: meshRotation.y - 90, z: meshRotation.z }, //The angle to which the model needs to be rotated
    duration: 1000,             // Animation duration in milliseconds
    delay: 100,                 // Animation start delay in milliseconds
    executions: 1,              // Number of animation executions
    reversePlay: false,         // Whether to play in reverse
    resetOnComplete: false      // Whether to return to initial position after completion
});
```
 
**Example:**

Write the above code on the button, click the button to play the model rotation animation. 





![1](../../../../assets/images/3d_lowcode_object_gmodel_rotateto1.gif)