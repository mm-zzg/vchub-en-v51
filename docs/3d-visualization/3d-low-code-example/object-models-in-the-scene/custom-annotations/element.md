# element

**Description: Modify the element of a custom annotation**

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene()// Get the scene in the 3D viewer control
let div = document.createElement('div')// Create a container for HTML elements
div.style.transform = 'scale(10)'// DIV amplification by ten times
//Title
let head = document.createElement('p')// Create a paragraph to display the title
head.style.textAlign = 'center'// Align text center
head.style.padding = '5px'// Text spacing
head.innerHTML = 'NewHtmlMarker'// Text content
div.appendChild(head)// Add title to container

const HTML = await scene.findHtml({name:'HTML1'})// Find model
HTML.element = div// Modify div
```
 
**Example:**

Write the above code on the button, click the button to modify the custom annotated element.

![1](../../../../assets/images/3d_lowcode_object_cAnnotations_element1.gif)



