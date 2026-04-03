# System.UI.forward


## Description

Call this function to return to the previous page after System.UI.back().

## Grammar

**System.UI.forward(): void**

 - Parameter

    Nothing

- Return

    Nothing

## Code Example 

Execute the script System.UI.open('B') on Page A to open Page B.

```typescript 

System.UI.open('B');
```  
Execute the script System.UI.back() on Page B to return to Page A.

```typescript 
System.UI.back();

```   
Execute the script System.UI.forward() on Page A to return to Page B.

```typescript 
System.UI.forward();

```   
