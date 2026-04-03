# Batch Update

After batch creating data on the **Model** or **Instance** page, you can update the detailed settings for the tags. This includes configurations such as alarm settings for tags and binding the data source paths for the tags.

## Export Tags

1. In the batch operation window of the **Model** or **Instance**, click the "Batch Operation" button.
    ![alt text](14.png)
    ![alt text](15.png)
2. In the batch operation popup, click the "Export Tags" button.
    ![alt text](16.png)
3. After clicking, a tag selector will pop up, allowing you to add the tags to be exported into the "Selected List". If a directory or instance is selected, it means that all tags under that directory or instance node (including the current node and all its child nodes) are selected. When a directory or instance is selected, an asterisk (*) is used to indicate all tags under it.
    ![alt text](17.png)
4. Click the "OK" button to open the property selection window, where you can choose the tag properties to be exported. The exported file will be in Excel format. 
    ![alt text](18.png)

## Import Tags

After modifying the exported tag file, click the "Import Tags" button in the batch operation pop-up to import the tags.

![alt text](19.png)

**Notes:**

- This operation will match the tags in the asset using the data in the path column of the Excel file, overriding the tag configurations. It does not support adding or deleting tags.
- For configurations that do not need to be updated, you can either delete the corresponding columns in the Excel file or set the values of the corresponding columns to empty.
- Tags referenced from the Type will have their modified configurations overwritten during the import tag configuration operation.

## Tag Configuration Excel

 Tag configuration form contains all the configuration items of the tag (except thename and data type), the user in the export of the tag configuration, modify the contents of the form, and then import the tag configuration, tag configuration can be realized in a batch update.

 Some of these configurations are complex configurations, which will be a complex object in actual storage. In ta g c onfiguration excel, we use a regular string to simplify it: *Key1=Value1,Key2=Value2,Key3=Value3.*

**An example:**

 Need to be configured in a column at the same time **Name, Age, Address**  three field values, then only need to fill in the cell *Name = Tom, Age = 18, Address= Unknow* can be.

 Complex objects for the collection of cases, it is only necessary to multiple object string to ";" can be separated, such as:

*Name=Tom,Age=18,Address=Unknow; Name=Peter, Age=19,Address=Unknow*

**Note** : Key and Value values in  complex configurations do not support '='.

 Complex configurations encountered in the following tables will first be commented as"Complex Configuration" or "Complex Collection Configuration" in the description.

| **Type**    | **Column Names**   | **Description**    |
|-------------|------------------|-------------------|
| Path   | Path   | The complete path of the tag, when importing tag configuration, the system will match the tags in the asset based on the path .    |
| Basic  configuration       | Description                         | Tag description configuration, users can fill in any string according to their needs.  |
|                            | TagGroup                            | The tag group configuration of the tag needs to correspond to the data name of the tag group module when modifying, otherwise it will cause the tag function to fail.   |
|                            | InitialValue                        | When initializing tags, the default value is pushed. When modifying, the type ofthe tag should be considered, such as a Double type tag, which cannot be changed to a string.   |
|                            | EngineeringLowLimit                 | Theoretical minimum value for numeric tag. Other types of tags do not apply. Paired with engineering high limit, it  will participate in tag operations.     |
|                            | EngineeringHighLimit               | Theoretical  maximum value for numeric tag. Other types of tags do not apply. Paired with engineering low limit, it  will participate in tag operations.   |
|                            | Unit                                | Numeric tags can be configured and input strings can be customized.    |
|                            | Writable                            | Enter True or False to configure the tag as writable.   |
| I/O Tag Data Source        | DataSource                          | I/O tags can be configured to bind to specific device data source .  |
| Expression Tag Data Source | SourceTagPath                           | The expression tag is configurable and can be directly inputted as p ath or selected as a tag. Only one tag can be selected .    |
|                            | Expression(Read)                    | Only expression tags display this property. Required, defaults to displaying {Source}, where {Source} represents the value of the source tag. The new value obtained by calculating the source tag through an expression can be used as the read value of the current tag.   |
|                            | Expression(Write)                   | Only expression tags display this property. Required, defaults to displaying {Value}, where {Value} represents the original value of the source tag. This expression determines the value that should be written to the tag.     |
| History                    | HistoryRecordEnabled                | Whether the tag records history can be filled in True or False. When updating the history configuration of tags, the system will use this column as the initial judgment basis. That is to say, if this column does not exist in the import file, the system will not recognize the data in the "history"related column and update it to the tag.   <br>When exporting, all "history" related columns in the table will exist.If you need to update the history during import, please ensure that all"history" related columns exist in the table, otherwise it may cause configuration errors.  |
|                            | HistoryRecordMode                   | History record mode, optional fields:   <br>-  On Change:Storage upon tag change <br>-  Periodic:Storage based on fixed intervals   <br>-  Raw:Store the original value of the tag |
|                            | HistoryRecordStoragePeriod          | The storage period to be filled in when the history mode is periodic.     |
|                            | HistoryRecordStoragePeriodUnit      | When the history mode is periodic, the storage period unit that needs to be filled in is used in conjunction with the "Storage Period".    <br>Optional fields:   <br>-  Milliseconds <br>-  Seconds <br>-  Minutes <br>-  Hours <br>-  Days <br>-  Weeks <br>-  Months <br>-  Years    |
|                            | HistoryRecordCompressMode | History storage compression mode, optional:   <br>-  Off <br>-  Delta Compression  <br>-  Slope Compression    |
|                            | HistoryRecordCompressType       | When the history compression mode is Delta Compression, it needs to be filled in, and can be optionally filled in:   <br>-  Absolute   <br>-  Percentage  |
|                            | HistoryRecordCompressValue   | When the compression mode is set to "Delta Compression" or "Slope Compression", configuration is required. Enter a positive number. |
|                            | HistoryRecordTimeoutFallbackEnabled         | When the history mode is delta storage or when the history mode is periodic storage and the compression mode is not Off, it can be configured. Select True or False to indicate whether it is turned on or off.    |
|                            | HistoryRecordFallbackInterval           | When the history record timeout compensation is enabled as True, it needs to be configured and any positive number should be filled in.    |
|                            | HistoryRecordFallbackIntervalUnit          | When the historical record timeout replenishment is set to True, it needs to be configured with a replenishment interval, which is used in conjunction withthe historical record timeout replenishment interval.    <br>Optional fields:   <br>-  Milliseconds <br>-  Seconds <br>-  Minutes <br>-  Hours <br>-  Days <br>-  Weeks <br>-  Months <br>-  Years  |
| Deadband | DeadbandEnabled                     | Whether the tag has a collection deadband enabled, you can choose to fill in True or False. When updating the collection deadband configuration of tags, the system will use this column as the initial judgment basis. That is to say, ifthis column does not exist in the import file, the system will not recognizethe data in the "deadband " related column and update it to the tag.   <br>When exporting, all "deadband" related columns in the table will exist. If you need to update the collection deadband during import, please ensure that all "deadband" related columns exist in the table, otherwise it may cause configuration errors.    |
|                            | DeadbandMode                        | Collect deadband detection mode, optional to fill in:   <br>-  Absolute  <br>-  Percentage     |
|                            | DeadbandValue               | Collect the specific value of the deadband  range and fill in a positive number.   <br>-  When the deadband mode is Absolute, it represents the deadband value , <br>-  When the deadband  mode is Percentage, it represents the percentage of deadband. If 1 is filled in, it is 1%.      |
| Scale                      | ScaleEnabled                        | Whether to enable range scale for numerical or Bool tags can be filled in as True or False. When updating the range scale configuration of a tag, the system will use this column as the initial judgment basis. That is to say, if this column does not exist in the import file, the system will not recognize the data in the range scale related column being updated to the tag.   <br>When exporting, all range scale related columns in the table will exist. If range scale needs to be updated during import, please ensure that all range scale related columns exist in the table, otherwise it may cause configuration errors.   |
|                            | ScaleMode                          | Range scale calculation method, optional to fill in:   <br>-  Linear: can be selected when the tag type is number <br>-  Square: Square root, can be selected when the tag type is number <br>-  Reverse: Reverse, can be selected when the tag type is bool   |
|                            | ScaleValueMin                   | When the range scale mode is Linear or Square, it needs to be configured to participate in the calculation of range scale and fill in any numerical value.   |
|                            | ScaleValueMax                          | When the range scale mode is Linear or Square, it needs to be configured to participate in the calculation of range scale and fill in any value greater than the minimum range scale value.  |
|                            | ScaleRawMin                         | When the range scale mode is Linear or Square, it needs to be configured to participate in the calculation of range scale and fill in any numerical value.   |
|                            | ScaleRawMax                         | When the range scale mode is Linear or Square, it needs to be configured to participate in the calculation of range scale and fill in any value greater than the minimum original value of range scale.   |
| Event                     | EventEnabled                        | Whether the tag opens an event, you can choose to fill in True or False. When updating the event configuration of tags, the system will use this column as the initial judgment basis. That is to say, if this column does not exist in the import file, the system will not recognize the data in the"event" related column being updated to the tag.    <br>When exporting, all "event" related columns in the table will exist. If an event needs to be updated during import, please ensure that all"event" related columns exist in the table, otherwise it may cause configuration errors.   |
|                            | EventSetValue                       | You can choose to fill in True or False. When filled in as True, writing a value to the tag will trigger an event log.    |
|                            | EventSetValueLog                    | When the write value of the event tag is set to True, it can be configured and filled in any string.  |
|                            | EventValueChanged                   | Bool type tags are configurable and can be filled in either True or False. When filled in as True, an event log will be triggered when the value of the bool tag changes.  |
| Simulate                  | SimulateEnabled                   | Whether the tag is enabled for simulation, you can choose to fill in True or False.When updating the simulation configuration of tags, the system will use this column as the initial judgment basis. That is to say, if this column does not exist in the import file, the system will not recognize the data in the"simulate" related column being updated to the tag.    <br>When exporting, all simulation related columns in the table will exist. If you need to update the simulation during import, please ensure that all simulation related columns exist in the table, otherwise it may cause configuration errors.  |
|                            | SimulateType                      | Simulation method, optional to fill in:   <br>-  Fixed:Fixed  <br>-  Random:Random, optional for numerical, Boolean, and character tags  <br>-  Increment:Incremental, optional for numerical tags  <br>-  Decrement:Decrement, numerical tags can be optionally matched  <br>-  Reverse:Reverse, Boolean tag optional  <br>-  Cycle:Loop, optional for character type tags  <br>-  CurrentTime: Real time value, optional temporal tag    |
|                            | SimulateInitialValue              | When the simulation type is **Fixed, Random, Increment, Decrement, Reverse, Cycle**,it can be configured, and the corresponding type of value needs to be filled in according to the tag value type. For example, numerical tags can only be filled in with numerical values, otherwise the tag will encounter runtime errors after updating.   |
|                            | SimulateValueMin                | When the simulation type is: **Random, Increment, Decrement**, it can be configured and any value can be filled in.    |
|                            | SimulateValueMax               | When the simulation type is: **Random, Increment, Decrement** can be configured,fill in any value greater than the minimum simulation value.   |
|                            | SimulateDecimals                  | When the simulation type is **Fixed, Random, Increment, Decrement**, and the tag type is Double , it can be configured and can be filled with values ranging from 0 to 16.  |
|                            | SimulateChangeFrequency           | When the simulation type is: **Random, Increment, Decrement, Reverse, Cycle**, it can be configured and a positive integer can be filled in.    |
|                            | SimulateChangeAmplitude           | When the simulation type is: **Increment, Decrement** can be configured, and any value can be filled in.      |
|                            | SimulateSimulationValue           | When the tag is of String type and the simulation mode is **Cycle or Random**, it can be configured to fill in the string used for character type tag simulation operations. <br>For example, if it is necessary to simulate random push of a, b,c, then the cell can be filled with "a, b, c" (without double quotation marks)   |
| Custom Properties          | CustomEnabled                       | Whether the tag has custom properties enabled, you can choose to fill in True or False. When updating the custom attribute configuration of a tag, the system will use this column as the initial judgment basis. That is to say, if this column does not exist in the import file, the system will not recognize the data in the "custom attribute" related column and update it to the tag.   <br>When exporting, all columns related to "custom properties" will exist inthe table. If you need to update custom properties  during import, please ensure that all columns related to "custom properties" exist in the table, otherwise it may cause configuration errors.    |
|                            | CustomArray                  | **Complex configuration**   <br>Each custom propertie has 2 fields to fill in:   <br>-  key:The name of the custom property <br>-  Value:Custom property  value     |
| Alarm                      | AlarmEnabled                        | Whether the tag has enabled the alarm property, you can choose to fill in True or False. When updating the alarm attribute configuration of a tag, the system will use this column as the initial judgment basis. That is to say, if this column does not exist in the import file, the system will not recognize thedata in the "alarm" related column being updated to the tag.    <br>When exporting, all alarm related columns in the table will exist. If alarm properties need to be updated during import, please ensure that all alarm related columns exist in the table, otherwise it may cause configuration errors. |
|                            | AlarmLimitInclusive                 | When the tag type is a numerical tag, it can be configured and can be optionally filled in:   <br>-  Open    <br>-  Closed       |
|                            | AlarmLimitDelay                     | **Complex configuration**    <br>Can be configured when the tag type is a numerical tag.   <br>-  ActiveDelayEnabled:Enable activation delay  <br>-  ActiveDelay:Activation delay time (ms)  <br>-  RecoveryDelayEnabled:Enable recovery delay  <br>-  RecoveryDelay:Recovery delay time (ms)  |
|                            | AlarmRateOfChangeDelay              | **Complex configuration**    <br>Can be configured when the tag type is a numerical tag.  <br>-  ActiveDelayEnabled:Enable activation delay  <br>-  ActiveDelay:Activation delay time (ms)  <br>-  RecoveryDelayEnabled:Enable recovery delay  <br>-  RecoveryDelay:Recovery delay time (ms)   |
|                            | AlarmEquivalentDelay               | **Complex configuration**    <br>Can be configured when the tag type is numeric or character tag.   <br>-  ActiveDelayEnabled:Enable activation delay  <br>-  ActiveDelay:Activation delay time (ms)  <br>-  RecoveryDelayEnabled:Enable recovery delay  <br>-  RecoveryDelay:Recovery delay time (ms)   |
|                            | AlarmSettings x                | **Complex configuration**   <br>Due to the fact that the number of alarm configurations in the system can be customized by users to increase or decrease, and due to the complexity of alarm configuration items, Excel adopts a multi column approach to display alarm configurations, with column names named "AlarmConfiguration+Number". <br>For example, if a tag opens a limit alarm and an equivalent alarm, then when exporting, there will be "AlarmConfiguration 1" and "Alarm Configuration 2" in the table,storing limit alarm configuration and equivalent alarm configuration respectively.   |


**Detailed Description of Alarm Configuration**

| **Alarm Type** | **Tag Type** | **Description**    |
|--------------|-----------------|-----------------|
| Limit Alarm               | Number                | -  Key:Limit alarm number, from low 4 to high 4 corresponds to 1-8  <br>-  Enabled:Enable current limit alarm <br>-  Name:Alarm name  <br>-  Limit:Alarm limit  <br>-  Priority:Alarm level, Low, Medium, High, Critical <br>-  DeadBand:Alarm Deadband  <br>-  DeadBandMode:Alarm Deadband Mode  <br>-  AckMode:Alarm confirmation mode, Auto - automatic, Manual - manual (no confirmation required), ManualNeedInfo - manual (confirmation required)  <br>-  Description:Alarm Description  <br>-  AlarmType: Required as Limit  |
| Change of Rate Alarm         | Number                  | -  Enabled:Enable the current rate of change alarm <br>-  Name:Alarm name  <br>-  Rate:Change rate (%)  <br>-  Cycle:Cycle  <br>-  CycleUnit:Cycle unit, optional to fill in Milliseconds, Seconds, Minutes, Hours, Days,Weeks, Months, Years  <br>-  Priority:Alarm level,  Low,  Medium, High , Critical <br>-  AckMode:Alarm confirmation mode, Auto <br>- automatic, Manual - manual (no confirmation required), ManualNeedInfo - manual (confirmation required)  <br>-  Description:Alarm Description  <br>-  AlarmType: Required as RateChange |
| Equivalent Alarm          | Number,String           | -  Enabled:Enable the current equivalent alarm  <br>-  Name:Alarm name  <br>-  Value:Value  <br>-  Priority:Alarm level,  Low,  Medium, High , Critical <br>-  AckMode:Alarm confirmation mode, Auto - automatic, Manual - manual (no confirmation required), ManualNeedInfo - manual (confirmation required)  <br>-  Description:Alarm Description  <br>-  AlarmType: Required as Equivalent  |
| On/Off Alarm           | Bool                    | -  TrueToFalseName:Enable on to off alarm  <br>-  TrueToFalseName:On to Off Alarm Name <br>-  TrueToFalsePriority:On to Off Alarm Level, Low,  Medium, High , Critical <br>-  TrueToFalseAckMode:On to Off Alarm Confirmation Mode, Auto - Automatic, Manual - Manual (no confirmation required), ManualNeedInfo - Manual (confirmation required)  <br>-  TrueToFalseDescription:On to Off Alarm Description  <br>-  FalseToTrueName:Enable off to on alarm  <br>-  FalseToTrueName:Alarm name from off to on  <br>-  FalseToTruePriority:Switch off to on alarm level, Low,  Medium, High , Critical <br>-  FalseToTrueAckMode:Switch off to on alarm confirmation mode, Auto - automatic, Manual - manual(no confirmation required), ManualNeedInfo - manual (confirmation required)  <br>-  FalseToTrueDescription:Alarm description from off to on  <br>-  AlarmType: Required as BooleanJump |


