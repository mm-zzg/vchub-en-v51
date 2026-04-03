# Tag

 In VC Hub, tags refer to measurable and actionable data or states of the monitoring and control process. These tags can be various types of information,such as temperature, pressure, flow, current, voltage, switching status, etc.,which are used to reflect the real-time status or performance of the monitored object.

 In a VC Hub system, tags are the basic building blocks of the system, and their values can be collected by sensors, meters or other data sources. Real-time data from these tags are collected, stored, displayed and analyzed by the VC Hub system, enabling operators to effectively monitor and control the monitored objects.

 Tags can be created in the Asset window of the designer. Each tag has a number of properties , such as alarms, history, etc. After you create tags, you can use them in controls, scripts, or reports.

 Here is a simple example of a control binding a tag. The tag "Temperature" is bound to a LED Display control , and the value of the temperature is displayed on it in realtime.

![alt text](1.png)

## **Tag Characteristics**

 Tags have the following features in VC Hub:

-  Object-oriented design. By instantiating the model, tags can be created in batches, saving time.
-  Powerful alarm model. Any number of alarms can be configured on each tag. Various types of alarms are supported, including limit alarms, rate-of-change alarms,equal-value alarms, and switching trip alarms.
-  History Record . The History module makes it easy to store and use historical data.Simply turn on history record for a tag and the historical data will be stored in the database in a valid format. The data can then be queried and displayed through scripts, historical chart , reports, etc.

## **Tag Naming**

-  Names need to be unique within the same level .
-  Names can only contain English letters, Chinese characters, numbers and underscores,and begin with English letters or Chinese characters only.
-  Case sensitive, which means that Temperature and temperature are treated as two different tags.
-  The length must not exceed 20 characters.

 To increase maintainability and readability, it is recommended to use descriptive,meaningful tag names. This helps others to more easily understand the use and meaning of the tag.

  


