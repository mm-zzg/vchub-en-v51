# System.Datatable.toDatatable


## Description

Transform data from third-party APIs or databases into datatable object.

## Grammar

**System.Datatable.toDatatable(data: Array`<any>`, headers?: Array`< string>`): Datatable**<br>

 - Parameter<br>
    data<br>
    headers - Column names are required if 'data' is a two-dimensional array.<br>
- Return<br>
    Datatable object<br>

## Code Example      

Scenario 1: Generate a data source from an array of objects that can be used in a table.
```typescript 
const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable([
    { studentId: 3, firstName: 'Charlie', lastName: 'Williams', gender: 'M', birthDate: '2000-05-30' },
    { studentId: 11, firstName: 'Kelly', lastName: 'Hernandez', gender: 'F', birthDate: '2000-01-25' },
    { studentId: 15, firstName: 'Mia', lastName: 'Gonzalez', gender: 'F', birthDate: '2001-04-06' }
]);
table1.applyChanges();


```   
Scenario 2: Generate a data source from a two-dimensional array that can be used in a table.
```typescript 
const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable([
    [3, 'Charlie', 'Williams', 'M', '2000-05-30'],
    [11, 'Kelly', 'Hernandez', 'F', '2000-01-25'],
    [15, 'Mia', 'Gonzalez', 'F', '2001-04-06']
], ['studentId', 'firstName', 'lastName', 'gender', 'birthDate']);
table1.applyChanges();


```   
