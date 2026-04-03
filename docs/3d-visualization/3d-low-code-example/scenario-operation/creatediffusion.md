# createDiffusion

**Description**: Create diffusion effects.



**Example1:** Create a radial sphere diffusion effect.

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
scene.createDiffusion({
    name: 'Diffusion', // Create the name of the diffusion
    type: 'Sphere', // Support 'Sphere' and 'Cylinder' to create spherical or cylindrical diffusion effects.
    color: '#ff0000', // Effect color
    radius: 50, // Initial radius
    height: 50, // Initial height
    diffuse: 10, // Diffusion ratio
    position: { x: 0, y: 0, z: 0 }, // Diffusion position
    duration: 3000,
    reversePlay: false // Reverse direction
})
```
 
Write the above code on the button, click the button, and you can create a spherical diffusion effect.

![3d_lowcode_SOperation_creatediffusion1](../../../assets/images/3d_lowcode_SOperation_creatediffusion1.gif)


**Example2:** Create a radial sphere diffusion effect.

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
scene.createDiffusion({
    name: 'Diffusion', // Create the name of the diffusion
    type: 'Cylinder', // Support 'Sphere' and 'Cylinder' to create spherical or cylindrical diffusion effects.
    color: '#ff0000', // Effect color
    radius: 50, // Initial radius
    height: 80, // Initial height
    diffuse: 5, // Diffusion ratio
    position: { x: 0, y: 0, z: 0 }, // Diffusion position
    duration: 3000,
    reversePlay: true // Reverse direction
})
```
 
Write the above code on the button, click the button, and you can create a cylindrical diffusion effect.

![3d_lowcode_SOperation_creatediffusion2](../../../assets/images/3d_lowcode_SOperation_creatediffusion2.gif)
