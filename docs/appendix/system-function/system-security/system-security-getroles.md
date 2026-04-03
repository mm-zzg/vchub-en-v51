# System.Security.getRoles


## Description

Get roles of the currently logged in user.

## Grammar

**System.Security.getRoles(): string**<br>

- Parameter <br>

    Nothing <br>

- Return <br>

    Roles, multiple roles separated by commas.<br>

## Code Example

Displays the role of the currently logged in person on a label.

```typescript 

const roles = System.Security.getRoles();
const label = await System.UI.findControl('Label1');
label.text = roles;
label.applyChanges();

```   
