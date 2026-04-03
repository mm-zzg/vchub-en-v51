# System.Tag.read


## Description

Get value, path, quality and timestamp of tag(s).

## Grammar

**System.Tag.read(path: string): Promise<{ path: string; value: any; time: string; quality: string; }>
System.Tag.read(paths: Array`<string>`): Promise`<Array<{ path: string; value: any; time: string; quality: string; }>>`**

- Parameter

    path - Tag path(s) 

- Return

    Value, path, quality and timestamp of tag(s)

## Code Example 

Get the value, path, quality and timestamp of the tag "Device:Temperature".

```typescript 
const tag = await System.Tag.read('@Device:Temperature');
console.log(tag.value);


```   
Get the value, path, quality and timestamp of tags 'Device:Temperature ' and 'Device:Power '.

```typescript 

const tags = await System.Tag.read(['@Device:Temperature', '@Device:Power']);
console.log(tags);
```   
