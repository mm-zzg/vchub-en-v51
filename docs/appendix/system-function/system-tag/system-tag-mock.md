# System.Tag.mock


## Description

Give a simulated value to the tag.

## Grammar

**System.Tag.mock(path:string, value:any): void**

- Parameter

     path - Tag path

     value - Simulated value 

- Return

     Nothing

## Code Example 

Generate a random integer between 0 and 99 and assign it to the tag "Device:Temperature".

```typescript 
const value = parseInt(`${Math.random() * 100}`);
System.Tag.mock('@Device:Temperature', value);

```   
