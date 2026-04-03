# Integration API definitions

## GET /api/v1/scripts/execute

Execute the custom script and return the result.

Protocol: Https

Request Payload(Json):

| Name       | Type      | Description                                                                                                           |
|------------|-----------|-----------------------------------------------------------------------------------------------------------------------|
| scriptName | String    | The custom script name                                                                                                |
| parameters | dynamic[] | The parameter list of the custom script, the paremeter type must much the actucl paramter type of the  custom script. |

Response Payload(JsonObject): The execution result of the custom script.

