

# System.Security.getUsername


## Description

Gets the username of the currently logged in user.

## Grammar

**System.Security.getUsername(): string**<br>

- Parameter<br>

    Nothing<br>

- Return<br>

    Username<br>

## Code Example

Displays the username of the currently logged in person on a label.

```typescript 

const user = System.Security.getUsername();
const label = await System.UI.findControl('Label1');
label.text = user;
label.applyChanges();

```   
