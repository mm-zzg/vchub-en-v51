






# movePaths

**Description: Model movement animation**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
const mesh = await scene.findMesh({ name: 'Forklift' });
const meshWorldPosition = mesh.getWorldPosition();
const paths = [
    { x: meshWorldPosition.x, y: meshWorldPosition.y, z: meshWorldPosition.z + 10 },
    { x: meshWorldPosition.x - 30, y: meshWorldPosition.y, z: meshWorldPosition.z + 10 },
    { x: meshWorldPosition.x - 30, y: meshWorldPosition.y, z: meshWorldPosition.z },
    { x: meshWorldPosition.x-10, y: meshWorldPosition.y, z: meshWorldPosition.z },
];
mesh.movePaths({
    worldPaths: paths,          // Path points for position animation
    faceForward: true,          // Model always faces movement direction
    duration: 3000,             // Animation duration in milliseconds
    delay: 100,                 // Animation start delay in milliseconds
    executions: 1,              // Number of animation executions
    reversePlay: false,         // Whether to play in reverse
    resetOnComplete: false      // Whether to return to initial position after completion
})
```
 
**Example:**

Write the above code on a button. When the button is clicked, the model movement animation will play.



![1](../../../../assets/images/3d_lowcode_object_gmodel_movepaths1.gif)