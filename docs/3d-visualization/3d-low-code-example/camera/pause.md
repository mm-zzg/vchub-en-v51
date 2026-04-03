# pause

**Description:：Pause the current camera animation.**

```typescript
const view = await System.UI.findControl('3DViewer1');
const scene = await view.getScene();
scene.camera.pause();
```
 
**Example:**

During the execution of the camera flyPaths animation, clicking the button pauses the current animation and restores the free-view mode.

![pause](../../../assets/images/pause.gif)