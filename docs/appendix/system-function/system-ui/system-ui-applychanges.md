# System.UI.applyChanges


## Description

Batch apply control changes.

## Grammar

**System.UI.applyChanges(controls: Array`<IControl>`, triggerLoadedEvent?:boolean): void**

- Parameter

    controls - Controls that need to apply changes

    triggerLoadedEvent - Whether to trigger the loaded event, This field is optional and defaults to false.

- Return

    Nothing

## Code Example 

When the boiler temperature is too high, display the alarm message on label1 and show the cooling message on label2.

```typescript 

const label1 = await System.UI.findControl('Label1');
label1.text = 'Boiler temperature is too high.';
label1.backgroundColor = 'red';
label1.fontColor = 'white';

const label2 = await System.UI.findControl('Label2');
label2.text = 'Cooling down...';

System.UI.applyChanges([label1, label2], false);

```   
