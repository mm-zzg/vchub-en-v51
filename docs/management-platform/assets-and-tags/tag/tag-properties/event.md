# Event

 By configuring the event properties of tags, the system can monitor issues that may require operator attention, such as equipment failures, out-of-range temperatures, and abnormal pressures. Events can also be audited and monitored,which can prevent security issues such as unauthorized access and data leakage.

## **How to Enable**

   In the add or edit  pop-up window of the tag, there is an event switch at the top, which is turned on for event setting.

![alt text](21.png)

 Different data types can set different categories of events.

![alt text](22.png)

| **Data Type** | **Set Value** | **Value Changed** |
|---------------|--------------------|-------------------|
| Integer       | √                  | X                 |
| Double        | √                  | X                 |
| Bool          | √                  | √                 |
| String        | √                  | X                 |
| DateTime      | √                  | X                 |

| **Name**      | **Description**                                                                                            |
|---------------|------------------------------------------------------------------------------------------------------------|
| Set Value     | After checking this option, an event will be recorded whenever a write operation is performed on this tag. |
| Value Changed | After checking this option, an event will be recorded whenever the value of the Boolean tag changes.       |

**Note:** The events recorded on the tag can be viewed in the Real-time Event and Historical Event. Set Value  can be viewed in "Operation Event" and the Value Changed  can be viewed in "Status Event". 




