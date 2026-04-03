

# System.UI.openPopup


## Description

Open a pop-up page.

## Grammar
  
**System.UI.openPopup(page: string, options: {
pageProperties?: any;      
position?: { type: 'center' | 'follow' | 'custom'; left?: number; top?: number; },      
titleBar?: {               
        title?: string;               
        backgroundColor?: string;               
        height?: number;             
        position?: 'left' | 'center' | 'right';              
        font?: 'Microsoft YaHei' | 'SimSun' | 'SimHei' | 'Arial' | 'Calibri' | 'Source Han Sans SC' | 'Georgia' | 'Tahoma' | 'Times New Roman' | 'Trebuchet MS' | 'Verdana' | 'Digital Numbers';              
        fontSize?: number;              
        fontColor?: string;             
        bold?: boolean;              
        italic?: number;              
      }
    }): Promise`<any>`**

- Parameter

    page - The name of the pop-up window that needs to be opened

    options - {
            
    pageProperties - Properties of page
            
    position - {
            
    type- pop up properties center screen, follow mouse, custom user-defined, 
            
    left- only needs to be filled in when type is custom, default 0 if not filled in,
            
    top- only needs to be filled in when type is custom, default 0 if not filled in
            
    }
            
    titleBar - {
            
    title - title content，
            
    backgroundColor - the background color of  title bar，
            
    height - the height of  title bar,
            
    position - title position：left/center/right，
            
    font - title font，
            
    fontSize - title font size，
            
    fontColor - title font color，
            
    bold - whether to use bold，
            
    italic - whether to use italics
        
    }

}

- Return

    Wait for pop-up closure and get the return value.

## Code Example 

**Scenario 1: Open the pop-up without waiting for it to close.**

Open a pop-up window named 'Details' at the center of the page, change the pop-up title to 'A0003 Details', and set the pop-up page property ID to 'A0003'.

```typescript 
System.UI.openPopup('Details', {
    pageProperties:{
      custom: {
          id: "A0003"
      }
    },
    position:{
        type: "center"
    },
    titleBar:{
        title: "A0003 Details"
    }
});


```
**Scenario 2: Open the pop-up and wait for it to close.**

Open a pop-up window named 'AddMaintenanceRecord' at a position 200 pixels from the left margin and 200 pixels from the top margin of the page. Change the pop-up title to 'Maintenance Details', and set the pop-up page properties: user to 'User005' and logDate to the current date. After the pop-up closes, navigate to the 'MaintenanceRecordList' page.
 
```typescript
const addResult  = await System.UI.openPopup('AddMaintenanceRecord', {
    pageProperties:{
      custom: {
          user: "User005",
          logDate: new Date().toLocaleDateString()
      }
    },
    position:{
        type: "custom",
        left: 200,
        top: 200,
    },
    titleBar:{
        title: "Maintenance Details"
    }
});

if(addResult === 'done'){
    System.UI.open('MaintenanceRecordList');
}

```
On the 'AddMaintenanceRecord' pop-up page, close the page and send a notification to the openPopup function after saving the data.
```typescript
//TODO (Save record to database by yourself)

System.UI.close('done');

```
