

# System.Tag.readValue


## Description

Read tag value(s).

## Grammar
**System.Tag.readValue(path: string): Promise`<any>`**

**System.Tag.readValue(path: Array`<string>`): Promise<{path: string; value: any}>**

- Parameter

    path - Tag path(s)

- Return

    Single tag value or multiple tag values and paths

## Code Example 

Get the value of the tag "Device:Temperature".

```typescript 
const tagValue = await System.Tag.readValue('@Device:Temperature');
console.log(tagValue);


```   
Get the path and the value of the tags "Device:Temperature" and "Device:Power".

```typescript 
const tags = await System.Tag.readValue(['@Device:Temperature','@Device:Power']);
console.log(tags);


```   
