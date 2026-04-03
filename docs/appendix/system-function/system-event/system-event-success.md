# System.Event.success

## Description

Add a successful operation event to the system event, which can be queried in real-time event control or historical event control.

## Grammar

System.Event.success(message:string,...args: any): Promise`<void>`

- Parameter <br>

    message - Description of the successful event <br>

    args - Detail of the successful event <br>

- Return <br>

    Nothing<br>

## Code Example 

Add a successful operation event.

```typescript 
// Add operation event description.
await System.Event.success('Lights turned off on schedule successfully.');

// Add operation event description and details.
await System.Event.success('Lights turned off on schedule successfully.', ['Meeting Room', 'Office Area', 'Reception']);


```   
