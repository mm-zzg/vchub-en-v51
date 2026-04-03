# setOutlineOption

**Description**: Set the edge parameters.

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const forklift = await scene.findMesh({ name: 'Forklift' });
const roboticArm01 = await scene.findMesh({ name: 'RoboticArm_01' });

scene.setOutlineOption({
    color: '#6ec800',
    edgeStrength: 7,
    edgeGlow: 1, 
    pulsePeriod: 5, // Breathing effect.
    selectObjects: [forklift, roboticArm01] // The model that requires outline.
});
```
 
**Example:**

Write the above code on a button. When the button is clicked, modify the edge parameters to apply outline to the model.

![1](../../../assets/images/3d_lowcode_SOperation_setoutlineoption1.gif)


