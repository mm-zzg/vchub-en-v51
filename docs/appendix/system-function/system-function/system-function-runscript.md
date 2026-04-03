# System.Function.runScript

## Description

Executes a user-defined custom function asynchronously within the system by its name. This method provides a flexible way to invoke custom logic, optionally passing an array of arguments, and returns a Promise that resolves with the function's result.

## Grammar

**System.Function.runScript(name: string, args?: Array`<any>`): Promise`<any>`**  

- Parameter <br>

    name - Custom function name  <br>

    args - Function parameters  <br> 

- Return  <br>

    Function result <br>

## Code Example

 Querying male students and displaying in a table.  
 ```typescript 
 const maleStudents = await System.Function.runScript('query-students', ['male']);  
 const table1 = await System.UI.findControl('Table1'); 
 table1.table = System.Datatable.toDatatable(maleStudents); 
 table1.applyChanges(); 
 ``` 

