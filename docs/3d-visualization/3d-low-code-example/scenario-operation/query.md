# query

**Description:** Query object in the scene

Query:

```typescript
const view = await System.UI.findControl('3DViewer1')// Obtain a 3D viewer control named "3DViewer1" in the page
const scene = await view.getScene();
const mash = await scene.query({
  //Id: "3b013f32-d6b0-484e-835c-e63e75d30ecb",//To query the unique uuid of the object
  name: 'Box2',//To query the name of the object
  type: 'Mesh',//To query the object type
  userData: {//To query the content of the object userData: Note: Query based on the key value pairs in userData, and the key value pairs need to match exactly
    test: "sth"
  }
})
console.log(mash)
```
 
**Example:**

Write the above code on the button, click the button to query the information of the created cube

![1](../../../assets/images/3d_lowcode_SOperation_query1.gif)

