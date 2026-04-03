

# System.Tag.writeValue


## Description

Write tag value(s).

## Grammar

**System.Tag.writeValue(path: string, newValue: any): Promise`<void>`
System.Tag.writeValue(path: string[], newValue: Array`<any>`): Promise`<void>`**

- Parameter

    path - Tag path(s) 

    newValue - Tag new value(s)

- Return

    Nothing

## Code Example 

Set 'Device:Start ' to true. 

```typescript 

await System.Tag.writeValue('@Device:Start', true);
```
Set 'Device:Start ' to true and 'Device:MaxPower ' to 500.


```typescript 

await System.Tag.writeValue(['@Device:Start', '@Device:MaxPower'], [true, 500]);
```   
