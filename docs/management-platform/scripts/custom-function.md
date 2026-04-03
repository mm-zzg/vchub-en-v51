# Custom Function

Custom functions are functions written by the user. Custom functions that can be called from within other scripts. The use of these functions can reduce the amount of repetitive code, thus reducing the maintenance workload of the application. It can not be directly triggered by the system, must be called through other script to perform, customized functions are divided into two types: **Generic Function** and **Service Ffunction**.

**Generic Function**: Generic function can be used in service scripts and ui scripts, use the `userDefined` namespace to access the custom functions that have been created.

**Service Function**: Service function are only used in service scripts. In the script, use the `userDefined` namespace to access the custom functions that have been created.

![alt text](12.png)

**Note**:   

1. A custom function must have one and only one `export function`, and the name of the `export function` is the name of the custom function. 
2. For a custom function, the name of the function must be unique. 
3. If needed, non-export functions can also be defined, but they cannot be called by external scripts. 
4. The name shown in the list is the name of the export function. 

You can create a custom function by clicking the "Add" button on the upper right corner of the list in the "**Scripts**" -> "**Custom Function**" page.

![alt text](11.png)

**Example**

1. Create a custom function named: getTagValue.<br>
    The script is as follows: 
    ```typescript
    export async function getTagValue() {
    const data = await System.Tag.read('@Default:Temperature')
    console.log(data)
    console.log(data.value)
    }
    ```   
2. Draw a button control on the page and write the following script in the control's mouse pressed action: 
    ```typescript
    userDefined.getTagValue()
    ```
3. Click the "Preview" button on the page, and this script will be executed when the button is pressed on the running page, and then the value of the tag will be printed on the console.

    ![custom](../../assets/images/custom.gif)