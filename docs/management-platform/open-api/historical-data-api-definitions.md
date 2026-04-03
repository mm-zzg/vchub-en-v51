# Historical Data API Definitions

## GET /api/v1/historicalData/tagValues

Get historical data of tag values

Protocol: Https

Request Payload(QueryString):

| Name            | Type     | Description                                                                                                          |
|-----------------|----------|----------------------------------------------------------------------------------------------------------------------|
| startTime       | DateTime | The start time                                                                                                       |
| endTime         | DateTime | The end time                                                                                                         |
| queryMode       | String   | The query mode(None,Raw,FixedPoints,Periodic)                                                                        |
| points          | Integer  | The query result count.                                                                                              |
| interval        | integer  | The sample period. The unit is second.                                                                               |
| period          | integer  | The sample period                                                                                                    |
| periodMode      | String   | The sample period mode(None,Second,Minute,Hour,Day)                                                                  |
| aggregationType | String   | The aggregation type, available values: Raw, Avg, Max, Min, First,Last,Count,CountOn,CountOff,DurationOn,DurationOff |
| path            | String[] | The tag path list                                                                                                    |

Response Payload(Json Array)

| Name    | Type     | Description            |
|---------|----------|------------------------|
| path    | String   | The tag path           |
| value   | Dynamic  | The tag value          |
| time    | DateTime | The timestamp          |
| quality | String   | The quality of the tag |

## GET /v1/historicalData/alarms

Get historical alarms

Protocol: Https

Request Playload(QueryString):

| Name         | Type     | Description                                                                                                                          |
|--------------|----------|--------------------------------------------------------------------------------------------------------------------------------------|
| providerName | String   | The history database provider name                                                                                                   |
| startTime    | DateTime | The start time                                                                                                                       |
| endTime      | DateTime | The end time                                                                                                                         |
| path         | String[] | The tag path list                                                                                                                    |
| priority     | String[] | The alarm priority list(Low,Medium,High,Critical)                                                                                    |
| state        | String[] | The alarm sate list(Active,Unacked,Acked,Cleared)                                                                                    |
| type         | String[] | The alarm type list(H ,H2 , H3,H4,L,L2,L3,L4,RateOfChange,Equivalent,TrueToFalse,FalseToTrue)                                        |
| asset        | String[] | The asset list                                                                                                                       |
| expression   | String   | Expression,Example1:priority == "Low", Example2:path.Contains("Device"), Example3:state.HasFlag("Active") &&stae.HasFlag("“Unacked") |

Response Payload(JsonArray):

| Name        | Type     | Description                                                                                |
|-------------|----------|--------------------------------------------------------------------------------------------|
| eventId     | String   | The id of the history record                                                               |
| path        | String   | The alarm path                                                                             |
| name        | String   | The alarm name                                                                             |
| type        | String   | The alarm type (H ,H2 , H3,H4,L,L2,L3,L4,RateOfChange,Equivalent,TrueToFalse,FalseToTrue ) |
| priority    | String   | The alarm priority (Low,Medium,High,Critical )                                             |
| eventTime   | DateTime | The time of the history record                                                             |
| status      | Status   | The alarm status(Active,Unacked;Active,Acked;Cleared,Unacked;Cleared,Acked)                |
| value       | Dynamic  | The tag value tiggered alarm                                                               |
| valueType   | String   | The value type of tag value                                                                |
| description | String   | The alrm description                                                                       |
| ackTime     | DateTime | The acknowledge time of the alarm                                                          |
| ackNotes    | String   | The notes of the alarm                                                                     |
| operator    | String   | The user who acknownlege the alarm                                                         |
| ackMode     | String   | The acknownledge mode (Auto,Manual,ManualNeedInfo)                                         |

## POST /v1/historicalData/alarms

Get historical alarms

Protocol: Https

Request Playload(JsonObject):

Field descriptions are the same as **GET /v1/historicalData/alarms**, only in POST format

Response Payload(JsonArray)):

The field descriptions are consistent with the response structure of **GET /v1/historicalData/alarms.**

## GET /v1/historicalData/pagedAlarms

Get paged historical alarms

Protocol: Https

Request Playload(QueryString):

| Name         | Type     | Description                                                                                                                          |
|--------------|----------|--------------------------------------------------------------------------------------------------------------------------------------|
| pageIndex    | Integer  | Current page number (starting from 1)                                                                                                |
| pageSize     | Integer  | Number of records returned per page                                                                                                  |
| providerName | String   | The history database provider name                                                                                                   |
| startTime    | DateTime | The start time                                                                                                                       |
| endTime      | DateTime | The end time                                                                                                                         |
| path         | String[] | The tag path list                                                                                                                    |
| priority     | String[] | The alarm priority list(Low,Medium,High,Critical)                                                                                    |
| state        | String[] | The alarm sate list(Active,Unacked,Acked,Cleared)                                                                                    |
| type         | String[] | The alarm type list(H ,H2 , H3,H4,L,L2,L3,L4,RateOfChange,Equivalent,TrueToFalse,FalseToTrue)                                        |
| asset        | String[] | The asset list                                                                                                                       |
| expression   | String   | Expression,Example1:priority == "Low", Example2:path.Contains("Device"), Example3:state.HasFlag("Active") &&stae.HasFlag("“Unacked") |

Response Payload(JsonObject):

| Name       | Type                     | Description                                                                                                    |
|------------|--------------------------|----------------------------------------------------------------------------------------------------------------|
| TotalCount | Integer                  | Total number of historical alarm records                                                                       |
| TotalPage  | Integer                  | Total number of pages of historical alarms                                                                     |
| Data       | AssetAlarmHistoryModel[] | List of alarm data, with the same field structure as the response payload of **GET /v1/historicalData/alarms** |

## POST /v1/historicalData/pagedAlarms

Get paged historical alarms

Protocol: Https

Request Playload(JsonObject)):

Field descriptions are the same as in **GET /v1/historicalData/pagedAlarms**, but in POST format only.

Response Payload(JsonObject):

The field descriptions are consistent with the response structure of **GET /v1/historicalData/pagedAlarms**