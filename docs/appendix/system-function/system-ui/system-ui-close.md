# System.UI.close


## Description

Close the current page.

## Grammar

**System.UI.close(data?: any): void**

- Parameter

    data - available when closing the pop-up page, returned as the value of the System.UI.openPopup function.

- Return

    Nothing

## Code Example

Close the current page.

```typescript 
System.UI.close();

```
Close the current popup page.

```typescript 
System.UI.close('Successfully added');
```
