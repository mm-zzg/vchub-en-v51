# System.UI.findControl


## Description

Find the control instance in the page.

## Grammar

**System.UI.findControl(name: string): any**

- Parameter

    name - The name of the control to be queried, and the control type can be inferred directly from the control name.

- Return

    Control instance

## Code Example

When the boiler temperature is too high, display the alarm message on label1.

```typescript 

const label1 = await System.UI.findControl('Label1');
label1.text = 'Boiler temperature is too high.';
label1.backgroundColor = 'red';
label1.fontColor = 'white';
label1.applyChanges();

```   
