
# System.Db.runSqlQuery

## Description

Execute SQL query to perform operations on the database.Before executing an SQL query to operate on the database, please refer to the [Create SQL Query](../../../2d-visualization/sql-query/create-sql-query.md) section to complete the SqlQuery setup.  

## Grammar

**System.Db.runSqlQuery(projectName: string, queryName: string, parameters?: Array<{ name: string, value: any}>): Promise`<any>`**

**System.Db.runSqlQuery(queryName: string, parameters?: Array<{ name: string, value: any}>): Promise`<any>`**

- Parameter <br>

    projectName - Project name, see code example below for usage <br>

    queryName - Query name   <br>    

    parameters - Query parameters <br>

- Return <br>
    
    Query result<br>

## Code Example  

**Query:** Query the database for male students and update the Table control.

```typescript 

// Scenario 1: Execute the SQL query in the current project
const maleStudents = await System.Db.runSqlQuery('query-students', [{
    name: 'gender',
    value: 'male'
}]);

const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable(maleStudents);
table1.applyChanges();


// Scenario 2: Execute an SQL query from another project, requires specifying the project name
// Scenario 3: Executing an SQL query in service script module, requires specifying the project name
const maleStudents = await System.Db.runSqlQuery('another-project-name', 'query-students', [{
    name: 'gender',
    value: 'male'
}]);

const table1 = await System.UI.findControl('Table1');
table1.table = System.Datatable.toDatatable(maleStudents);
table1.applyChanges();

```   
**Scalar Query:** Count the number of 12-year-old students and update the Label control.

```typescript 
// Scenario 1: Execute the SQL query in the current project
const count = await System.Db.runSqlQuery('number-of-students-by-age', [{
    name: 'age',
    value: 12
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = `${count} students`;
label1.applyChanges();


// Scenario 2: Execute an SQL query from another project, requires specifying the project name
// Scenario 3: Executing an SQL query in service script module, requires specifying the project name
const count = await System.Db.runSqlQuery('another-project-name', 'number-of-students-by-age', [{
    name: 'age',
    value: 12
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = `${count} students`;
label1.applyChanges();


```   
**Update Query:** Update Thomas's email to `thomas@example.com` and update the Label control.

```typescript 
// Scenario 1: Execute the SQL query in the current project
const updatedRowCount = await System.Db.runSqlQuery('update-student-email', [{
    name: 'name',
    value: 'Thomas'
}, {
    name: 'email',
    value: 'thomas@example.com'
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = updatedRowCount == 1 ? 'update success' : 'update failed';
label1.applyChanges();


// Scenario 2: Execute an SQL query from another project, requires specifying the project name
// Scenario 3: Executing an SQL query in service script module, requires specifying the project name
const updatedRowCount = await System.Db.runSqlQuery('another-project-name', 'update-student-email', [{
    name: 'name',
    value: 'Thomas'
}, {
    name: 'email',
    value: 'thomas@example.com'
}]);

const label1 = await System.UI.findControl('Label1');
label1.text = updatedRowCount == 1 ? 'update success' : 'update failed';
label1.applyChanges();
```   
