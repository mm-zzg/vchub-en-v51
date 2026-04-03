# System.Tag.getPropertyValues


## Description

Get the specified single or multiple node paths, property names, and property values.

## Grammar

**System.Tag.getPropertyValues(path: string): Promise<{ path: string; property: string; value: any }>System.Tag.getPropertyValues(path: Array`<string>`): Promise`<Array<{ path: string; property: string; value: any }>>`**

- Parameter<br>

     path - The path of a single or multiple node properties<br>

- Return<br>

     The path, property name, and value of a single or multiple node properties<br>

## Code Example  

Get the path of the node "Device: Temperature" and the value of the Name property.

```typescript 
const tagProperty = await System.Tag.getPropertyValues('@Device:Temperature#Name');
console.log(tagProperty);

``` 
Get the paths of the nodes "Device: Temperature" and "Device: Power" as well as the values of the "Name" property.

```typescript 

const tagProperties = await System.Tag.getPropertyValues(['@Device:Temperature#Name', '@Device:Power#Name']);
console.log(tagProperties);

```   
