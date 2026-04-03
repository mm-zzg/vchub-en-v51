# System.Library.getLocalImage


## Description

Get images from the local library.

## Grammar

**System.Library.getLocalImage(path:string): Promise`<string>`**

- Parameter<br>

    path - The path of the image<br>

- Return<br>

    base64<br>

## Code Example

Obtain"Sun. svg" from the local library under "Scenery".

```typescript 

const base64 = await System.Library.getLocalImage('Scenery.Sun.svg');
console.log(base64)
```   
