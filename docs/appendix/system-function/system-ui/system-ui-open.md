
# System.UI.open


## Description

Open a new page by replacing the window.

## Grammar

**System.UI.open(page: string, pageProperties?: any): void**

- Parameter

    page - The name of the page that needs to be opened.

    pageProperties - Properties of page.

- Return

    Nothing

## Code Example

Open page A.

```typescript 
System.UI.open('A');

```

Open page A and set its page property ID to 'A0003'.

```typescript 
System.UI.open('A', {
    custom: {
        id: "A0003"
    }
});


```  
