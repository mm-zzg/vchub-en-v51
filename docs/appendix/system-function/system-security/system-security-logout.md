

# System.Security.logout


## Description

Log out of the currently logged in user and return to the login page.

!!! note
    When debugging a page in Preview mode, calling `System.Security.login` or `System.Security.logout` performs a simulated action.
    `System.Security.login` only validates whether the username and password are correct.
    `System.Security.logout` does not perform an actual logout action.
    After a simulated successful login, subsequent behavior still runs under the current Design user.

## Grammar

**System.Security.logout(): Promise`<void>`** <br>

- Parameter <br>

    Nothing <br>

- Return <br>

    Nothing<br>

## Code Example

Logout.

```typescript 

System.Security.logout()

```   
