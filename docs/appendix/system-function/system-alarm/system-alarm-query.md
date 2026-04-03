# System.Alarm.query

## Description

Query real-time alarms. 

## Grammar

**System.Alarm.query(): Promise`<any>`<br>
System.Alarm.query(params?:{  
priority?: AlarmPriority | AlarmPriority[],<br>
state?: AlarmState | AlarmState[],<br>
path?: string | string[],<br>
type?:AlarmType | AlarmType[],<br>
asset?: string | string[],<br>
group?: string | string[],<br>
expression?: string}): Promise`<any>`**<br>
- Parameter<br>
  params - The query conditions object, optional parameters<br>
  {<br>
     priority? -  Priority(s), optional values are "Low","Medium","High","Critical"<br>
     state? - State(s), optional values are "Active","Unacked","Acked","Cleared"<br>
     path? - Alarm path(s)<br>
     type? - Type(s), optional values are "H","H2","H3","H4","L","L2","L3","L4","RateOfChange","Equivalent","TrueToFalse","FalseToTrue"<br>
     group? - Alarm group(s)<br>
     asset? - Asset(s)<br>
     expression? - Expression, Example1:priority == "Low", Example2:path.Contains("Device"), Example3:state.HasFlag("Active") && state.HasFlag("Unacked")<br>
   } <br>
- Return<br>
  [<br>
    {<br>
      path: string // Alarm path<br>
      name: string // Alarm name<br>
      type: string // Type<br>
      priority: string // Priority<br>
      eventTime: string // State change time<br>
      state: string // State<br>
      operator: string // Acknowledgment operator<br>
      valueType: string // Value type<br>
      value: string // Alarm value<br>
      ackTime: string  // Acknowledgment time<br>
      ackNotes: string // Acknowledgment notes<br>
      recoveryTime:string // Recovery time  description: string // <br>
      Description  ackMode: string // Acknowledgment mode<br>
      ruleName: string // Notification Rule  groupNames: string // Alarm group<br>
      activeTime: string // Activation time<br>
    },<br>
      ...<br>
  ] <br>


## Code Example 

Query all real-time alarms.  

```typescript 
const value = await System.Alarm.query();
console.log(value);
```   
Query real-time alarms with an alarm level of High, a type of H or H2, an alarm group of Default, and a status of "Active, Unacked".  

```typescript
const value = await System.Alarm.query({priority:"High",type:["H","H2"],group:'Default',expression:
'state.HasFlag("Active") && state.HasFlag("Unacked")'});
console.log(value);
``` 

