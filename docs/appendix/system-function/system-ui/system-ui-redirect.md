# System.UI.redirect


## Description

Redirect the page to a new URL.

## Grammar

**System.UI.redirect(url:string, newTab?: boolean)**

- Parameter

    url - The URL path that needs to be opened

    newTab - Whether to open as a new tab, default to true, can be left blank

- Return

    Nothing

## Code Example

Open google on the new tab. 

```typescript 

System.UI.redirect('https://www.google.com/');
```
Open google on the current tab. 

```typescript 
System.UI.redirect('https://www.google.com/', false);

```   
