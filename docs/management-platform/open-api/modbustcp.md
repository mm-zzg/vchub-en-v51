# ModbusTcp

## POST	api/v1/modbusTcp/device

Create new modbus tcp device

Protocol: Https

Request Payload:

| Name        | Type      | Description   |
|-------------|-----------|---------------|
| name        |String     |  name of device|
|ipAddress | string | ip or domain name|
| port  | Integer | port of device |
|connectionTimeout | Integer | device  connection Timeout|
| readTimeout  | Integer | device read Timeout |
| writeTimeout  | Integer | device  write Timeout|



## PUT	api/v1/modbusTcp/device

Update modbus tcp device

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
| id | String    | id of device |
| name |String   | name of device |
|ipAddress | string |  ip or domain name |
| port  | Integer | port of device |
|connectionTimeout | Integer | device  connection Timeout|
| readTimeout  | Integer | device read Timeout |
| writeTimeout  | Integer | device  write Timeout|


## GET	api/v1/modbusTcp/device/{deviceId}

Get modbus tcp device by device id

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|deviceId|string|device Id|


Response Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
| id | String    | id of device |
| name |String   | name of device |
|ipAddress | string |  ip or domain name |
| port  | Integer | port of device |
|isStarted|Boolean|the status of device|
|connectionTimeout | Integer | device  connection Timeout|
| readTimeout  | Integer | device read Timeout |
| writeTimeout  | Integer | device  write Timeout|


## DELETE	api/v1/modbusTcp/device/{id}

Delete modbus tcp device by id

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|Id|string| Id|


## DELETE	api/v1/modbusTcp/device/batch

Batch delete modbus tcp devices

Protocol: Https

Request Payload:
NA

Response Payload:
NA


## GET	api/v1/modbusTcp/export

Export modbus tcp by device id

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|deviceId|string|device Id|

Response Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|File |file|exported file|


## POST	api/v1/modbusTcp/frame

Create new modbus tcp frame

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|name|string|frame name|
|  area       | string | storage area |
| endAddress  | Integer | end Address of frame |
|startAddress | Integer | start Address of frame |
|slaveAddress | Integer | slave Address of frame |
|  frequency  | Double | frequency of frame |
|  deviceName | string | name of device |
| dataEncoding| string | data encoding style |


## PUT	api/v1/modbusTcp/frame

Update modbus tcp frame

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|  deviceName | string | name of device |
|slaveAddress | Integer | slave Address of frame |
| name|string|frame name|
|  area       | string | storage area |
|startAddress | Integer | start Address of frame |
| endAddress  | Integer | end Address of frame |
| dataEncoding| string | data encoding style |
|  frequency  | Double | frequency of frame |



## GET	api/v1/modbusTcp/frame/{deviceId}/{frameId}

Get modbus tcp frame by device id and frame id

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|deviceId|string|device Id|
|frameId|string|frame Id|

Response Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|id          |string|frame id|
| name|string|frame name|
|startAddress | Integer | start Address of frame |
| endAddress  | Integer | end Address of frame |
|  area       | string | storage area |
| dataEncoding| string | data encoding style |
|  frequency  | Double | frequency of frame |
|  deviceName | string | name of device |
|slaveAddress | Integer | slave Address of frame |


## DELETE	api/v1/modbusTcp/frame/{id}

Delete modbus tcp frame by id

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|deviceId|string|frame Id|
 

## 	GET	api/v1/modbusTcp/frames

Get modbus tcp frame list

Protocol: Https

Request Payload(Json):

| Name       | Type      | Description   |
|------------|-----------|---------------|
|DeviceId|string|device Id|
|SortOrder|string|sort by order|
|SortColumnName|string|sort by ColumnName|


Response Payload(Json):

| Name       | Type      | Description   |
|------------|-----------|---------------|
|id          |string|frame id|
| name|string|frame name|
|slaveAddress | Integer | slave Address of frame |
|  area       | string | storage area |
|startAddress | Integer | start Address of frame |
| endAddress  | Integer | end Address of frame |
| dataEncoding| string | data encoding style |
|  frequency  | Double | frequency of frame |
|  deviceName | string | name of device |
|creationTime|string|creation Time|


## 	GET	api/v1/modbusTcp/frames/{deviceId}

Get modbus tcp frames by device id

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|DeviceId|string|device Id|

Response Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|id          |string|frame id|
| name|string|frame name|
|startAddress | Integer | start Address of frame |
| endAddress  | Integer | end Address of frame |
|  area       | string | storage area |
| dataEncoding| string | data encoding style |
|  frequency  | Double | frequency of frame |
|  deviceName | string | name of device |
|slaveAddress | Integer | slave Address of frame |


## 	POST	api/v1/modbusTcp/import

Import modbus tcp file

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|File |file|Import file|


## GET	api/v1/modbusTcp/info

Get modbus tcp info by name

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|  Name | string | name of device |

Response Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|id          |string|frame id|
| name|string|frame name|
|ipAddress | string |  ip or domain name |
| port  | Integer | port of device |
|isReconnected|Boolean|the status of device|
|isStarted|Boolean|the status of device|
|connectionTimeout | Integer | device  connection Timeout|
| readTimeout  | Integer | device read Timeout |
| writeTimeout  | Integer | device  write Timeout|
|frameInfos|string||

| Name       | Type      | Description   |
|------------|-----------|---------------|
|id          |string|frame id|
| name|string|frame name|
|slaveAddress | Integer | slave Address of frame |
|  area       | string | storage area |
|startAddress | Integer | start Address of frame |
| endAddress  | Integer | end Address of frame |
| dataEncoding| string | data encoding style |
|  frequency  | Double | frequency of frame |
|  deviceName | string | name of device |
|creationTime|string|creation Time|


## POST	api/v1/modbusTcp/isStart/{deviceId}/{isStarted}

Start or stop modbus tcp server by device id

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|DeviceId|string|device Id|
|is Started|Boolean|the status of device|



## 	POST	api/v1/modbusTcp/isStartAll/{isStarted}

Start or stop all modbus tcp servers

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|is Started|Boolean|the status of device|


## 	GET	api/v1/modbusTcp/pageList

Get modbus tcp device paged list

Protocol: Https

Request Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|Name|string|Device name|
|PageIndex|integer|index of page|
|PageSize|integer|size of page|
|SortOrder|string|sort by order|
|SortColumnName|string|sort by ColumnName|


Response Payload:

| Name       | Type      | Description   |
|------------|-----------|---------------|
|id          |string|frame id|
| name|string|frame name|
|ipAddress | string |  ip or domain name |
| port  | Integer | port of device |
|isReconnected|Boolean|the status of device|
|isStarted|Boolean|the status of device|
|connectionTimeout | Integer | device  connection Timeout|
| readTimeout  | Integer | device read Timeout |
| writeTimeout  | Integer | device  write Timeout|
|frameInfos|string||

| Name       | Type      | Description   |
|------------|-----------|---------------|
|id          |string|frame id|
| name|string|frame name|
|slaveAddress | Integer | slave Address of frame |
|  area       | string | storage area |
|startAddress | Integer | start Address of frame |
| endAddress  | Integer | end Address of frame |
| dataEncoding| string | data encoding style |
|  frequency  | Double | frequency of frame |
|  deviceName | string | name of device |
|creationTime|string|creation Time|
