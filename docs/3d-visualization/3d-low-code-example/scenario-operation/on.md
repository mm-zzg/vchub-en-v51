# on

**Description: Subscribe to mouse or keyboard events** (mouse event support: 'click' |'mousedown’|'mouseup' |'mouseout '|'mouseover' keyboard event support: 'keydown' |'keyup’)

```typescript
//Script in the on button
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();// Get Scene
const chariot = await scene.findMesh ({name:'chariot'});// Find model
if (!chariot.userData?.off)// Determine whether an event has already been bound.
{
  const off = chariot.on('click', ()=>{console.log(123)});// Bind the click event and return the function to cancel the event
  chariot.userData = {off};// Save the off function in userDatd  
}

//Script in the off button
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();// Get Scene
const chariot = await scene.findMesh ({name:'chariot'});// Find model
if (chariot.userData.off)//Determine whether to subscribe to events
{
  chariot.userData.off();// Unsubscribe
}  
```
 
**Example:**

Write the above code on the button, click the on button to subscribe to the click event, and click the off button to unsubscribe.

![1](../../../assets/images/3d_lowcode_SOperation_on1.gif)





