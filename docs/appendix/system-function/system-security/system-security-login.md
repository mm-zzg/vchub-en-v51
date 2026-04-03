
# System.Security.login


## Description

Use this function to log in directly, avoiding the system's built-in login page.

## Grammar

**System.Security.login(username: string, password: string): Promise`<boolean>`**<br>

- Parameter<br>

    username<br>

    password<br>

- Return<br>

    Whether login succeeded.<br>

## Code Example

At the top of the page, there is a 'Switch User' button. Clicking the button opens the 'LoginPopup' popup. After the user enters their username and password and successfully login, the system automatically redirects to the project homepage.

Switch User Button Script

![alt text](a_sf_ss-login1.png)

```typescript 
const result = await System.UI.openPopup('LoginPopup');
if (result === 'GoHomePage') {
    System.UI.goHome();
}


```   
Login Button Script for the LoginPopup page

![alt text](a_sf_ss-login2.png)

```typescript 
const usernameInput = await System.UI.findControl('UsernameInput');
const passwordInput = await System.UI.findControl('PasswordInput');
const succeeded = await System.Security.login(usernameInput.text, passwordInput.text);
if (succeeded) {
    System.UI.close('GoHomePage');
}


```   


