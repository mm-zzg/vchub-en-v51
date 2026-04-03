# System.Alarm.queryHistory

## Description

Query the historical alarms of the current historical storage.

## Grammar


**System.Alarm.queryHistory(historyStorage:string): Promise`<any>`<br>
System.Alarm.queryHistory(historyStorage:string,params:{<br>
startTime?: Date | string,<br>
endTime?: Date | string,<br>
priority?: AssetAlarmPriority | AssetAlarmPriority[],<br>
state?: AssetAlarmState | AssetAlarmState[],<br>
path?: string | string[],<br>
type?: AssetAlarmType | AssetAlarmType[],<br>
asset?: string | string[],<br>
expression?: string}): Promise`<any>`**<br>
- Parameter<br>
      historyStorage - Name of the history storage<br>
      params  - The query conditions object, optional parameters<br>
      {<br>
           startTime? - Start time, default is 8 hours before the current time<br>
           endTime? - End time, default is the current time<br>
           priority? -  Priority(s), optional values are "Low","Medium","High","Critical"<br>
           state? - State(s), optional values are "Active","Unacked","Acked","Cleared"<br>
           path? - Alarm path(s)<br>
           type? - Type(s), optional values are "H","H2","H3","H4","L","L2","L3","L4","RateOfChange","Equivalent","TrueToFalse","FalseToTrue"<br>
           asset? - Asset(s)<br>
           expression? - Expression, Example1:priority == "Low", Example2:path.Contains("Device"), Example3:state.HasFlag("Active") && state.HasFlag("Unacked")  <br>       
      }<br>
- Return<br>
[<br>
         {<br>
            path: string // Alarm path<br>
            name: string // Alarm name<br>
            type: string // Type<br>
            priority: string // Priority<br>
            eventId: string // State change ID<br>
            eventTime: string // State change time<br>
            state: string // State<br>
            operator: string // Acknowledgment operator<br>
            valueType: string // Value type<br>
            value: string // Alarm value<br>
            ackTime: string  // Acknowledgment time<br>
            ackNotes: string // Acknowledgment notes<br>
            ackMode: string // Acknowledgment mode<br>
            nodeName: string // Node name<br>
            storageName: string // History storage name<br>
            description: string // Description<br>
           },<br>
          ...<br>
]<br>


## Code Example

Query the historical alarms from the "Default" historical storage for the past 8 hours. 

```typescript 
const value = await System.Alarm.queryHistory("Default");
console.log(value);
```   
Query the historical alarms from the "Default" historical storage within the time range from 2025-03-10 00:00:00 to 2025-03-11 00:00:00, with an alarm level of High, a type of H or H2, and a status of "Active, Unacked".

```typescript
const value = await System.Alarm.queryHistory("Default",{startTime:'2025-03-10 00:00:00',endTime:'2025-03-11 00:00:00',priority:"High",type:["H","H2"],expression:'state.HasFlag("Active") && state.HasFlag("Unacked")'});
console.log(value);
``` 

