# Expression Function

## What is an expression function?

Expression functions are predefined functions that can be called in multiple places within a project. When you execute an expression function, you can pass parameters to it to get the execution result, which helps avoid writing the same logic repeatedly.

Expression functions are located under "Project > Function" in the editor.

![alt text](1.png)

## Create Expression Function

To create an expression function, right-click on the "Expression Function" node under "Function" and select "Add".

![alt text](3.png)


![alt text](2.png)

**Note**：In use, Expression function is referred to by name, so all references to the expression function need to be updated when renaming.

**Property**

| **Name**    | **Description**   |
|-------------|-------------|
| Description | Description of expression function. |
| Script      | **Note:**  <br>1. An expression function must contain one and only one `export function`. The name of this export function serves as the name of the expression function. <br>2. Names of expression functions must be unique across all functions. <br>3. If needed, non-export functions can be defined within the expression function, but they cannot be called by external scripts. <br>4. The name displayed in the list corresponds to the name of the export function. <br>5. Expression functions only support the two system functions `tag` and `property`. All functions under the `System` namespace are **not supported**. <br>6. Expression functions and page functions are independent of each other and **cannot call one another**. |

## **Where can expression functions be used?**

In any property binding interface that supports **Expression**, you can access expression functions through the `ExpressionFunction` namespace.

![alt text](4.png)

**Example:** Tank alarm level determination

1. Create an expression function named `getTankAlarmLevel` with the following script

    ```typescript
    // @param {number} level - Current level
    // @param {number} maxLevel - Maximum level
    // @returns {number} Alarm level: 0-Normal, 1-Warning, 2-Alarm
    export function getTankAlarmLevel(level: number, maxLevel: number) {
        if (level >= maxLevel * 0.9 || level <= maxLevel * 0.1) {
            return 2; // Alarm
        } else if (level >= maxLevel * 0.8 || level <= maxLevel * 0.2) {
            return 1; // Warning
        }
        return 0; // Normal
    }
    ```
    
2. Add a rectangular control to the page, click the bind button of background color, and bind the expression property. The script is as follows:

    ```typescript
    const currentLevel = tag('@Default:currentLevel');
    const alarmLevel = ExpressionFunction.getTankAlarmLevel(currentLevel, 10);

    if(alarmLevel === 2){
      return "#FF0000";// Red - Alarm
    }

    if(alarmLevel === 1){
      return "#FFFF00";// Yellow - Warning
    }

    return "#00FF00";//  Green - Normal
    ```