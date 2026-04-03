# Stale Alarm

 The purpose of stale alarm configuration is to reduce unnecessary alarm interference, and you should try to avoid stale alarms during engineering configuration. 

 Stale alarm are mainly for the following 2 situations:

1.  For alarms that have been active for a long time (regardless of whether theyare manually acknowledged or automatically acknowledged), the system will automatically acknowledge the alarm even if the alarm has not disappeared after the stale alarm is set for a longer period of time than the stale alarm. The start of the stale alarm calculation time is the moment the alarm is generated.
2.  For alarms that require manual acknowledgement, if the user does not acknowledge the alarm for a long time after the alarm returns to normal, the system will automatically acknowledge the alarm after it reaches the length of time set for stale alarm. The stale start time is counted from the time the alarm returns to normal, not from the time the alarm is generated.

   You can set the obsole scence time on the "**Alarming** " -> "**Stale Alarm** " screen. Alarms that reach the configured duration are considered  stale alarms.

![alt text](5.png)

| **Name**                  | **Description**                                                                              |
|---------------------------|----------------------------------------------------------------------------------------------|
| Alarm Retention Period(h) | The duration for which an alarm remains active if it is not handled or acknowledged in time. |

