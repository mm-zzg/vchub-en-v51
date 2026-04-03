
# System.Library.getSystemImage


## Description

Obtain images from the system library.

## Grammar

**System.Library.getSystemImage(path:string): Promise`<string>`** 

- Parameter <br>

    path - The path of the image  <br>

- Return <br>

    base64<br>

## Code Example

Obtain"Transformer. svg" under "Power" in the system library.

```typescript 
const base64 = await System.Library.getSystemImage('Power.Transformer.svg');
console.log(base64)


```   

