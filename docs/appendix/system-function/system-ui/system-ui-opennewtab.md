

# System.UI.openNewTab


## Description

Open the page in a new tab.

## Grammar

**System.UI.openNewTab(page: string, pageProperties?: any): void**

- Parameter

    page - The name of the page that needs to be opened

    pageProperties - Properties of page.

- Return

    Nothing

## Code Example

Open page A on a new browser tab

```typescript 
System.UI.openNewTab('A');

```
Open page A on a new browser tab and set its page property ID to 'A0003'.

```typescript 

System.UI.openNewTab('A', {
    custom: {
        id: "A0003"
    }
});

```   
