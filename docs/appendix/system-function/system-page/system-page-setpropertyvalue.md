
# System.Page.setPropertyValue


## Description

Set the value of the current page's custom property or control property.

## Grammar

**System.Page.setPropertyValue(path: string,value: any): void** 

- Parameter <br>

    path - Path of the page's custom property or control property <br>

    value - New value <br>

- Return <br>

    Nothing<br>

## Code Example 

Get the value of the custom property "no" on the page, and add 1 to its value each time.

```typescript 
const value = System.Page.getPropertyValue('#custom.no');
System.Page.setPropertyValue('#custom.no', value > 100 ? 0 : value + 1);


```   
Set the text property of TextInput1 to 'WAGO VC Hub'.

```typescript 
System.Page.setPropertyValue('TextInput1#text', 'WAGO VC Hub');



```   

