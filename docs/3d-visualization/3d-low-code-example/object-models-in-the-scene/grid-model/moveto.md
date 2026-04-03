
# moveTo

**Description: Model displacement animation**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const mesh = await scene.findMesh({ name: 'Forklift' });
const meshWorldPosition = mesh.getWorldPosition();
mesh.moveTo({
   worldPosition: { x: meshWorldPosition.x, y: meshWorldPosition.y, z: meshWorldPosition.z +10},//The world coordinates that the model needs to move to
    duration: 3000,             // Animation duration in milliseconds
    delay: 100,                 // Animation start delay in milliseconds
    executions: 2,              // Number of animation executions
    reversePlay: false,         // Whether to play in reverse
    resetOnComplete: false      // Whether to return to initial position after completion
})
```
 
**Example:**

Write the above code on the button, click the button to play the model displacement animation. 






![1](../../../../assets/images/3d_lowcode_object_gmodel_moveto1.gif)