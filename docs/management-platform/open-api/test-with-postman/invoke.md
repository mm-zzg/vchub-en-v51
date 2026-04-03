# Call the HTTPS API

Open API provides Web APIs over the HTTPS protocol, with the default HTTPS port set to 10443.

1. Before creating an HTTP request for Open API in Postman, browse the API definitions on the Swagger documentation page. Please refer to chapter [API Document(Swagger)](../api-document-swagger.md).

    The API definitions also can be found on chapter 

    - [Asset API Definitions](../asset-api-definitions.md)
    - [Historical Data API Definitions](../historical-data-api-definitions.md)
    - [Realtime Data API Definitions](../realtime-data-api-definitions.md)
    - [Integration API Definitions](../integration-api-definitions.md)

        ![alt text](9.png)

2. Create a new request in Postman UI according to API definitions.

    ![alt text](10.png)

3. Open the **Authorizaiton** Tab, select **Bearer Token** from the Auth Type dropdown list, and enter the access token in the **Token** text box.

    ![alt text](11.png)

4. Click the **Send** button, the API returns the response with success status code.

    ![alt text](12.png)



