
# System.Tag.queryPropertyValues


## Description

Get the child nodes path, property name, and property value of a specific property for the direct(non-recursive)  child nodes under a specified parent path.

## Grammar

**System.Tag.queryPropertyValues(tagParentPath:string,property:string): Promise`<Array<{ path: string; property: string; value: any }>>`**

- Parameter

     tagParentPath - Parent path

     property  - Property name

- Return

     Path, name, and value of the direct child node property

## Code Example 

Get the paths of all direct child nodes under the path "Device: Device 1" , as well as the values of the Name property of the child nodes.

```typescript 

const tagProperties = await System.Tag.queryPropertyValues('@Device:Device1','Name');
console.log(tagProperties);

```   
