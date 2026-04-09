# Asset API Definitions

## GET /api/v1/assetInstances

Get asset instances 

Protocol: Https

Request Payload(QueryString):

| Name       | Type   | Description                                        |
|------------|--------|----------------------------------------------------|
| parentPath | String | The parent path used to filter the asset instances |

Response Payload:

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| treeName   | String | Asset tree name                           |
| parentPath | String | The parent path of current asset instance |
| name       | String | Asset model instance name                 |
| type       | String | Asset type (Folder,Instance)              |
| modelPath  | String | The model path of current instance        |



## POST /api/v1/assetInstances

Create asset instance 

Protocol: Https

Request Payload:(JsonObject)

| Name       | Type   | Description                                   |
|------------|--------|-----------------------------------------------|
| parentPath | String | The parent path of current asset instance     |
| name       | String | Asset instance name                           |
| modelPath  | String | The referenced model path of current instance |



## PUT /api/v1/assetInstances/{path}

Update asset instance by path  

Protocol: Https

Request Payload:(JsonObject)

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| parentPath | String | The parent path of current asset instance |

Response Payload: NA


## DELETE /api/v1/assetInstances/{path}

Delete asset instance by path 

Protocol: Https

Path Parameter:

| Name | Type   | Description                       |
|------|--------|-----------------------------------|
| path | String | The path of current asset instance |

Response Payload: NA


## GET /api/v1/assetInstances/{path}/properties

Get properties of asset instance by instance path, the properties means the child items of asset instance. 

Protocol: Https

Path Parameter:

| Name | Type   | Description                       |
|------|--------|-----------------------------------|
| path | String | The path of current asset instance |


Response Payload:

| Name        | Type               | Description                                                                                                           |
|-------------|--------------------|-----------------------------------------------------------------------------------------------------------------------|
| treeName    | String             | Asset tree name                                                                                                       |
| parentPath  | String             | Parent path of current asset instance property                                                                        |
| name        | String             | Asset instance name                                                                                                   |
| path        | String             | Full path of instance property                                                                                        |
| modelPath   | String             | The referenced model path of current instance property, only has value when the type of current property is Instance  |
| type        | String             | Asset type (Instance,Tag)                                                                                             |
| tagType     | String             | Tag type (IO,Memory,Expression,System), only has value when the type of current property is Tag                       |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag |
| description | String             | The instance property description, only has value when the type of current property is Tag                            |
| properties  | AssetModelProperty | The child properties of current property                                                                              |


## POST /api/v1/assetInstances/batch

Batch add asset instance api.

Protocol: Https

Request Payload:(JsonArray)

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
| name       | String | Asset instance name                       |
|parentPath|string|Parent path of current asset instance|
|modelPath|string|The model path of current instance |

| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


## PUT /api/v1/assetInstances/batch

Batch Update Asset Instances

Protocol: Https

Request Payload:(JsonArray)

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
| name       | String | Asset instance name                       |
|parentPath|string|Parent path of current asset instance|
|modelPath|string|The model path of current instance |

| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


## DELETE /api/v1/assetInstances/batch/delete

Batch Delete Asset Instances by paths

Protocol: Https

Request Payload:(JsonArray)

| Name | Type     | Description                               |
|------|----------|-------------------------------------------|
| data | String[] | The asset instance path list to be deleted |

Response Payload: NA


## POST /api/v1/assetInstances/batch/query

Batch get asset tags by parent path.

Protocol: Https

Response Payload:

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |     Asset tree name                  |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |


| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||

|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |



## POST /api/v1/assetInstances/customProperties

Get instance custom properties

Protocol: Https

Request Payload(QueryString):

| Name       | Type   | Description                                     |
|------------|--------|-------------------------------------------------|
|AssetTree|string|The Asset Tree of instance|
| Paths | String | The path of instance|

Response Payload(JsonArray)

| additionalProp1    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp2    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp3    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


## PUT	/api/v1/assetInstances/customProperties

Update the custom properties of instances

Protocol: Https

Request Payload(QueryString):

| Name       | Type   | Description                                     |
|------------|--------|-------------------------------------------------|
|AssetTree|string|The Asset Tree of instance|
| CustomProperties |   |    |

| additionalProp1    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp2    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp3    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|



## GET /api/v1/assetModels

Get asset models 

Protocol: Https

Request Payload(QueryString):

| Name       | Type   | Description                                     |
|------------|--------|-------------------------------------------------|
| parentPath | String | The parent path used to filter the asset models |

Response Payload(JsonArray)

| Name       | Type   | Description                    |
|------------|--------|--------------------------------|
| treeName   | String | Asset tree name                |
| parentPath | String | Parent path of Asset model     |
| name       | String | Asset model name               |
| type       | String | Asset type (Type,Instance,Tag) |
| path       | String | Full path of asset model       |



## POST /api/v1/assetModels

Create new asset model

Protocol: Https

Request Payload(JsonObject):

| Name       | Type   | Description                |
|------------|--------|----------------------------|
| parentPath | String | Parent path of Asset model |
| name       | String | Asset model name           |

Response Payload: NA



## PUT /api/v1/assetModels/{modelPath}

Update Asset model path model path

Protocol: Https

Request Payload(JsonObject):

| Name | Type   | Description      |
|------|--------|------------------|
| name | String | Asset model name |

Response Payload: NA



## DELETE /api/v1/assetModels/{modelPath}

Delete Asset mdoel by model path.

Protocol: Https

Path Parameter:

| Name      | Type   | Description           |
|-----------|--------|-----------------------|
| modelPath | String | The asset model path |

Response Payload: NA



## GET /api/v1/assetModels/{modelPath}/properties

Get properties of the Asset model by model path, the properties means the child items of the Asset model 

Protocol: Https

Request Payload(QueryString):

| Name       | Type   | Description                |
|------------|--------|----------------------------|
| parentPath | String | Parent path of Asset model |

Respose Payload(JsonArray):

| Name        | Type               | Description                                                                                                           |
|-------------|--------------------|-----------------------------------------------------------------------------------------------------------------------|
| treeName    | String             | Asset tree name                                                                                                       |
| parentPath  | String             | Parent path of Asset model                                                                                            |
| name        | String             | Asset model name                                                                                                      |
| path        | String             | Full path of model property                                                                                           |
| modelPath   | String             | the model path of model instance, only has value when the property type is Instance                                   |
| type        | String             | Asset type (nstance,Tag)                                                                                              |
| tagType     | String             | Tag type (IO,Memory,Expression,System)                                                                                |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag |
| description | String             | The model property description                                                                                        |
| properties  | AssetModelProperty | The child properties of current property                                                                              |



## POST /api/v1/assetModels/{modelPath}/properties

Create new Asset model property 

Protocol: Https

Request Payload(JsonObject):

| Name        | Type   | Description                                                                                                           |
|-------------|--------|-----------------------------------------------------------------------------------------------------------------------|
| name        | String | Asset model property name                                                                                             |
| type        | String | Asset type (Instance,Tag)                                                                                             |
| modelPath   | String | the model path of model instance, only has value when the property type is Instance                                   |
| tagType     | String | Tag type (IO,Memory,Expression,System), only has value when the type of current property is Tag                       |
| valueType   | String | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag |
| description | String | The model property description                                                                                        |

Response Payload: NA



## PUT /api/v1/assetModels/{modelPath}/properties/{name}

Update asset model property by the model path and name  

Protocol: Https

Request Payload(JsonObject):

| Name        | Type   | Description                    |
|-------------|--------|--------------------------------|
| name        | String | Asset model property name      |
| description | String | The model property description |

Response Payload: NA



## DELETE /api/v1/assetModels/{modelPath}/properties/{name}

Delete asset model property by model path and name 

Protocol: Https

Request Payload: NA 

Response Payload: NA


## POST /api/v1/assetModels/{modelPath}/properties/batch

Create new Asset model properties by batch

Protocol: Https

Request Payload(JsonArray):

| Name        | Type   | Description                                                                                                           |
|-------------|--------|-----------------------------------------------------------------------------------------------------------------------|
| name        | String | Asset model property name                                                                                             |
| type        | String | Asset type (Instance,Tag)                                                                                             |
| modelPath   | String | the model path of model instance, only has value when the property type is Instance                                   |
| tagType     | String | Tag type (IO,Memory,Expression,System), only has value when the type of current property is Tag                       |
| valueType   | String | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag |
| description | String | The model property description                                                                                        |



## POST	api/v1/assetModels/batch

Batch create new asset models

Protocol: Https

Request Payload(JsonArray):

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The description of current asset models |
|customProperties|||
| name       | String | Asset models name                       |
|parentPath|string|Parent path of current asset models|


| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|



## PUT	api/v1/assetModels/batch

Batch update asset models. The model must contain the path of asset model to be updated.

Protocol: Https

Request Payload(JsonArray):

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The description of current asset models |
|customProperties|||
| name       | String | Asset models name                       |
| Path|string|Parent path of current asset models|


| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


## DELETE	api/v1/assetModels/batch/delete

Batch delete asset models by model paths

Protocol: Https

Request Payload(JsonArray):

| Name | Type     | Description                               |
|------|----------|-------------------------------------------|
| data | String[] | The asset model path list to be deleted |

Response Payload:NA


## POST	api/v1/assetModels/batch/query

Batch Query AssetModel Properties

Protocol: Https

Response Payload:


| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |           Asset tree name              |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |
|properties|String|AssetModel Properties|

| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||


|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |



## POST	api/v1/assetModels/customProperties

Get the custom properties of Models

Protocol: Https

Response Payload(QueryString):

| additionalProp1    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp2    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp3    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


## PUT	api/v1/assetModels/customProperties

Update the custom properties of Models

Protocol: Https

Request Payload(QueryString):

| Name       | Type   | Description                                     |
|------------|--------|-------------------------------------------------|
|AssetTree|string|The Asset Tree of instance|
| CustomProperties |   |    |

| additionalProp1    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp2    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

| additionalProp3    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|

## POST	api/v1/assetModels/properties/batch

Batch Add AssetModel Properties

Protocol: Https

Request Payload:

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |         Asset tree name                |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |
|properties|String|AssetModel Properties|


| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||

|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |


## PUT	api/v1/assetModels/properties/batch

Batch Update AssetModel Properties


Protocol: Https

Request Payload:

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |             Asset tree name            |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |
|properties|String|AssetModel Properties|


| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||

|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |

## DELETE	api/v1/assetModels/properties/batch/delete

Batch Delete AssetModel Properties.

Protocol: Https

Request Payload: NA

Response Payload: NA

## POST	api/v1/assetModels/properties/batch/query

Batch Query AssetModel Properties

Protocol: Https

Response Payload: 


| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |                       |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |
|properties|String|AssetModel Properties|


| customProperties    |    |                                |
|------------|--------|-------------------------------------------|
|additionalProp1|string|custom property1|
|additionalProp2|string|custom property2|
|additionalProp3|string|custom property3|


|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||

|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |


## GET /api/v1/assets

Description: Get All Assets, the assets means the root trees

Protocol: Https

Request Payload: NA 

Response Payload(JsonArray):

| Name        | Type   | Description       |
|-------------|--------|-------------------|
| id          | String | Asset id          |
| name        | String | Asset name        |
| description | String | Asset description |


## POST /api/v1/assets

Create new Asset

Protocol: Https

Request Payload(JsonObject):

| Name        | Type   | Description       |
|-------------|--------|-------------------|
| name        | String | Asset name        |
| description | String | Asset description |

Response Payload: NA


## PUT /api/v1/assets/{id}

Update asset by id. 

Protocol: Https

Request Payload(JsonObject):

| Name        | Type   | Description       |
|-------------|--------|-------------------|
| name        | String | Asset name        |
| description | String | Asset description |

Response Body: NA

## DELETE /api/v1/assets/{id}

Delete asset tree by asset tree id

Protocol: Https

Path Parameter:

| Name | Type   | Description       |
|------|--------|-------------------|
| id   | String | The asset tree id |

Response Body: NA



## POST	api/v1/assets/batch

Batch Create new Asset Tree.

Protocol: Https

Request Payload(JsonArray):

| Name        | Type   | Description       |
|-------------|--------|-------------------|
| name        | String | Asset name        |
| description | String | Asset description |
|historyDatabase|String|Select history Database |


## PUT	api/v1/assets/batch

Batch update asset trees. The model must contain the id of asset tree to be updated.

Protocol: Https

Request Payload(JsonArray):

| Name        | Type   | Description       |
|-------------|--------|-------------------|
| name        | String | Asset name        |
| description | String | Asset description |
|historyDatabase|String|Select history Database |
|id           |String  |id of asset tree    |

Response Payload(JsonArray):

| Name          | Type   | Description|
|---------------|--------|------------|
|additionalProp1|String  |Possible existed error messages|
|additionalProp2|String  |Possible existed error messages|
|additionalProp3|String  |Possible existed error messages|


## DELETE	api/v1/assets/batch/delete

Batch Delete asset tree by ids

Protocol: Https

Request Payload(JsonArray):

| Name | Type     | Description                       |
|------|----------|-----------------------------------|
| data | String[] | The asset tree id list to delete |

Response Payload: NA


## GET /api/v1/tags

Get asset tags that includes normal tags and tags within instance 

Protocol: Https

Request Payload(QueryString):

| Name       | Type   | Description                         |
|------------|--------|-------------------------------------|
| parentPath | String | The parent path used to filter tags |

Response Payload(JsonArray):

| Name        | Type   | Description                                                                                                           |
|-------------|--------|-----------------------------------------------------------------------------------------------------------------------|
| treeName    | String | Asset tree name                                                                                                       |
| parentPath  | String | Parent path of current item                                                                                           |
| name        | String | Asset instance name                                                                                                   |
| path        | String | Full path of tag                                                                                                      |
| modelPath   | String | The reference model path of current instance property, only has value when the type of current item is Instance       |
| type        | String | Asset type (Folder,Instance,Tag)                                                                                      |
| tagType     | String | Tag type (IO,Memory,Expression,System), only has value when the type of current property is Tag                       |
| valueType   | String | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag |
| description | String | The tag description, only has value when the type of current item is Tag                                              |



## POST  /api/v1/tags

Create new asset Tag 

Protocol: Https

Request Payload(JsonObject):

| Name        | Type   | Description                                                                                                           |
|-------------|--------|-----------------------------------------------------------------------------------------------------------------------|
| parentPath  | String | Parent path of current tag                                                                                            |
| name        | String | Asset instance name                                                                                                   |
| type        | String | Asset type (Folder,Instance,Tag)                                                                                      |
| tagType     | String | Tag type (IO,Memory,Expression,System)                                                                                |
| valueType   | String | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag |
| description | String | The tag description                                                                                                   |



## PUT /api/v1/tags/{path}

Update Tag by path 

Protocol: Https

Request Payload(JsonObject):

| Name        | Type   | Description                |
|-------------|--------|----------------------------|
| parentPath  | String | Parent path of current tag |
| name        | String | Asset instance name        |
| description | String | The tag description        |

## DELETE /api/v1/tags/{path}

Delete tag by path 

Protocol: Https

Request Payload: NA 

Response Payload: NA



## GET /api/v1/tags/{path}/configuration

Get tag configuration

Protoco: Https

Request Payload: NA

Response Payload(JsonObject):

| Name        | Type                         | Description                   |
|-------------|------------------------------|-------------------------------|
| name        | String                       | Tag name                      |
| tagGroup    | String                       | Tag group                     |
| description | String                       | Description of the tag        |
| value       | ValueConfigurationModel      | Value configuration           |
| alarm       | AlarmConfigurationModel      | Alarm configuration           |
| history     | HistoricalConfigurationModel | history configuartion         |
| deadband    | DeadbandConfigurationModel   | Deadband configuration        |
| scale       | ScaleConfigurationModel      | Scale configuration           |
| event       | EventConfigurationModel      | Event configuration           |
| simulate    | SimulationConfigurationModel | Simulation configuration      |
| custom      | CustomConfigurationModel     | Custom property configuration |

Value Configuration Model(ValueConfigurationModel)

| Name                 | Type    | Description                                    |
|----------------------|---------|------------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |

Alarm Configuration Model(AlarmConfigurationModel)

| Name              | Type                                | Description                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |

Limit Alarm Configuration Model(LimitAlarmConfigurationModel)

| Name               | Type              | Description             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |

Limit Alarm Model(LimitAlarmModel)

| Name             | Type    | Description                                                                             |
|------------------|---------|-----------------------------------------------------------------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |

Rate Of Change Alarm Configuration Model(RateOfChangeAlarmConfigurationModel)

| Name               | Type                     | Description                   |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |

Rate Of Change Alarm Model(RateOfChangeAlarmModel)

| Name             | Type    | Description                                                                             |
|------------------|---------|-----------------------------------------------------------------------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |

Equivalent Alarm Configuration Model(EquivalentAlarmConfigurationModel)

| Name               | Type                   | Description               |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |

Equivalent Alarm Model(EquivalentAlarmModel)

| Name             | Type    | Description                                                                             |
|------------------|---------|-----------------------------------------------------------------------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |

Boolean Alarm Configuration Model(BooleanAlarmConfigurationModel)

| Name               | Type                |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |

Boolean Alarm Model(BooleanAlarmModel)

| Name             | Type    | Description                                                                             |
|------------------|---------|-----------------------------------------------------------------------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |

Historical Configuration Model(HistoricalConfigurationModel)

| Name                 | Type    | Description                                                   |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |

Deadband Configuration Model(DeadbandConfigurationModel)

| Name          | Type    | Description            |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

Scale Configuration Model(ScaleConfigurationModel)

| Name     | Type   | Description                        |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |

Event Configuration Model(EventConfigurationModel)

| Name                | Type    | Description                   |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |

Simulation Configuration Model(SimulationConfigurationModel)

| Name            | Type    | Description                                                                 |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

Custom Configuration Model(CustomConfigurationModel)

| Name    | Type          | Description               |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |

Custom Model(CustomModel)

| Name  | Type    | Description           |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |





##	POST	api/v1/tags/batch

Batch Add asset tags

Request Payload: 


| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |          Asset tree name              |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |

|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||


|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |




## 	PUT	api/v1/tags/batch

Batch Update asset tags

Request Payload: 


| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |         Asset tree name               |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |


|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||


|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |


##  DELETE	api/v1/tags/batch/delete

Batch Delete Asset Tag by paths

Protocol: Https

Request Payload: NA 

Response Payload: NA


## 	POST	api/v1/tags/batch/query

Batch Add asset tags

Request Payload: 


| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| description | String | The parent path of current asset instance |
|customProperties|||
| treeName       | String |             Asset tree name            |
|parentPath|string|Parent path of current asset instance|
| name       | String | Asset instance name                       |
| type        | String             | Asset type (Instance,Tag)    |
| path        | String             | Full path of model property   |
|modelPath|string|The model path of current instance |
| tagType     | String             | Tag type (IO,Memory,Expression,System)     |
| valueType   | String             | Tag value type (Unknown,Integer,String,Double,Bool,DateTime), only has value when the type of current property is Tag  |
|  configuration |  |  |

|  configuration |  |  |
|------------|--------|-------------------------------------------|
| name       | String |Name of asset tag |
|  tagGroup | String | Selected tagGroup of asset tag|
|  description | string | description of asset tag |
|  value |  |  |
|  alarm |  |  |
|  history |  |  |
|  deadband |  |  |
|  scale |  |  |
|  event |  |  |
|  simulate |  |  |
|custom|||


|  value |  |  |
|------------|--------|-------------------------------------------|
| valueType            | String  | Data type(Integer,String,Double,Bool,DateTime) |
| initialValue         | Dynamic | Initial value                                  |
| engineeringLowLimit  | Double  | Engineering low limit                          |
| engineeringHighLimit | Double  | Engineering high limit                         |
| unit                 | String  | Unit                                           |
| writable             | Boolean | Writable tag value                             |
| dataSource           | String  | Data source                                    |
| dataSourcePath       | String  | Data source path                               |
| readExpression       | String  | Read expression                                |
| writeExpression      | String  | Write expression                               |



| Alarm              |                              |                        |
|-------------------|-------------------------------------|------------------------------------|
| limitAlarm        | LimitAlarmConfigurationModel        | Limit alram configuration          |
| rateOfChangeAlarm | RateOfChangeAlarmConfigurationModel | Rate of change alarm configuration |
| equivalentAlarm   | EquivalentAlarmConfigurationModel   | Equivalent alarm configuration     |
| booleanAlarm      | BooleanAlarmConfigurationModel      | Boolean alarm configuration        |



| LimitAlarm               |                |             |
|--------------------|-------------------|-------------------------|
| activeDelayEnabled | Boolean           | Enable activation delay |
| activeDelay        | Integer           | Activation delay time   |
| resumeDelayEnabled | Boolean           | Enable resume delay     |
| resumeDelay        | Integer           | Resume delay time       |
| inclusive          | String            | Inclusion mode          |
| limitAlarms        | LimitAlarmModel[] | List of limit alarms    |


| LimitAlarms      |         |                                   |
|------------------|---------|-----------------------------------|
| enabled          | Boolean | Enable limit alarm                                                                      |
| type             | String  | Type(H ,H2 , H3,H4,L,L2,L3,L4)                                                          |
| name             | String  | Limit alarm name                                                                        |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| limit            | Double  | Limit value                                                                             |
| deadband         | Double  | Deadband value                                                                          |
| deadbandMode     | String  | Deadband mode                                                                           |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| RateOfChangeAlarm               |                  |                    |
|--------------------|--------------------------|-------------------------------|
| activeDelayEnabled | Boolean                  | Enable activation delay       |
| activeDelay        | Integer                  | Activation delay time         |
| resumeDelayEnabled | Boolean                  | Enable resume delay           |
| resumeDelay        | Integer                  | Resume delay time             |
| rateOfChangeAlarms | RateOfChangeAlarmModel[] | List of rate of change alarms |
 

| RateOfChangeAlarms |      |                  |
|------------------|---------|-----------------------------|
| enabled          | Boolean | Enable rate of change alarm                                                             |
| name             | String  | Rate of change alarm name                                                               |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| changeRate       | Double  | Change rate(%)                                                                          |
| cycle            | Double  | Cycle time                                                                              |
| cycleUnit        | String  | Cycle unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)                                       |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| EquivalentAlarm               |                |             |
|--------------------|------------------------|---------------------------|
| activeDelayEnabled | Boolean                | Enable activation delay   |
| activeDelay        | Integer                | Activation delay time     |
| resumeDelayEnabled | Boolean                | Enable resume delay       |
| resumeDelay        | Integer                | Resume delay time         |
| equivalentAlarms   | EquivalentAlarmModel[] | List of equivalent alarms |


| EquivalentAlarm             |      |                     |
|------------------|---------| --------------------------|
| enabled          | Boolean | Enable equivalent alarm                                                                 |
| name             | String  | Equivalent alarm name                                                                   |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| Value            | Dynamic | Alarm value                                                                             |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| BooleanAlarm               |       |                         |
|--------------------|---------------------|-------------------------|
| activeDelayEnabled | Boolean             | Enable activation delay |
| activeDelay        | Integer             | Activation delay time   |
| resumeDelayEnabled | Boolean             | Enable resume delay     |
| resumeDelay        | Integer             | Resume delay time       |
| booleanAlarms      | BooleanAlarmModel[] | List of boolean alarms  |


| BooleanAlarms            |   |                     |
|------------------|---------| -----------------------------|
| enabled          | Boolean | Enable boolean alarm                                                                    |
| type             | String  | Alarm type                                                                              |
| name             | String  | Alarm name                                                                              |
| priority         | String  | Priority(Low,Medium,High,Critical)                                                      |
| ackMode          | String  | Acknowledgement mode(Automatic,Manual (No Confirmation),Manual (Requires Confirmation)) |
| notificationRule | String  | Notification rule                                                                       |
| description      | String  | Alarm description                                                                       |


| History                 |      |                                                     |
|----------------------|---------|---------------------------------------------------------------|
| mode                 | String  | Mode(On Change,Periodic)                                      |
| storagePeriod        | Integer | Storage period                                                |
| storagePeriodUnit    | String  | Storage period unit(Msec,Sec,Min,Hour,Day,Week,Month,Year)    |
| compressionMode      | String  | Compression mode(Off,Delta Compression,Slope Compression)     |
| compressionType      | String  | Compression type(Absolute,Percent)                            |
| value                | Double  | Value                                                         |
| timeoutFallback      | Boolean | Timeout fallback                                              |
| fallbackInterval     | Integer | Fallback interval                                             |
| fallbackIntervalUnit | String  | Fallback interval unit(Msec,Sec,Min,Hour,Day,Week,Month,Year) |
 

| Deadband          |     |              |
|---------------|---------|------------------------|
| mode          | String  | Mode(Absolute,Percent) |
| deadbandValue | Integer | Deadband value         |

  

| Scale     |     |                          |
|----------|--------|------------------------------------|
| mode     | String | Scale model(Linear,Square,Reverse) |
| rawMin   | Double | Minimum raw value                  |
| rawMax   | Double | Maximum raw value                  |
| valueMin | Double | Minimum scaled value               |
| valueMax | Double | Maximum scaled value               |
 

| Event                |      |                     |
|---------------------|---------|-------------------------------|
| setValueEnabled     | Boolean | Enable variable write value   |
| setValue            | String  | Value to set                  |
| valueChangedEnabled | Double  | Enable value change detection |
 

| Simulate         |      |                                                                  |
|-----------------|---------|-----------------------------------------------------------------------------|
| type            | String  | Simulation type(Fixed,Random,Increment,Decrement,Reverse,Cycle,CurrentTime) |
| initialValue    | Dynamic | Initial simulation value                                                    |
| simulationValue | String  | Simulation value                                                            |
| value           | Dynamic | Value                                                                       |
| minValue        | Double  | Minimum value                                                               |
| maxValue        | Double  | Maximum value                                                               |
| decimals        | Integer | Number of decimal places                                                    |
| changeFrequency | Integer | Frequency of value change                                                   |
| changeAmplitude | Double  | Amplitude of value change                                                   |

  
| Custom    |            |                 |
|---------|---------------|---------------------------|
| customs | CustomModel[] | List of custom properties |


| Customs  |      |             |
|-------|---------|-----------------------|
| name  | String  | Custom property name  |
| value | Dynamic | Custom property value |
|order  |Interger | Custom property order |