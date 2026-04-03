# resume

**Description:：Resume the previously paused camera animation.**

```typescript
const view = await System.UI.findControl('3DViewer1');
const scene = await view.getScene();
scene.camera.resume();
```
 
**Example:**

After pausing the camera flyPaths animation, clicking the button resumes the previously unfinished camera flyPaths animation.


![resume](../../../assets/images/resume.gif)
