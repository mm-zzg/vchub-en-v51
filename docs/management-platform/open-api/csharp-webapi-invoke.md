# Use C# to Invoke Open API (WebAPI)

This page shows a simple C# example for calling VC Hub Open API over HTTPS.

## Overview

The typical integration flow is:

1. Get OpenID Connect metadata from `/.well-known/openid-configuration`.
2. Read `token_endpoint` from the metadata response.
3. Request an access token by `client_credentials`.
4. Add `Authorization: Bearer {access_token}` to WebAPI requests.
5. Call Open API endpoints and process HTTP response payloads.

This example uses Asset API from [Asset API Definitions](asset-api-definitions.md):

- `GET /api/v1/assetInstances`
- `POST /api/v1/assetInstances`

## Prerequisites

- VC Hub Open API is enabled.
- You have `client_id` and `client_secret` from OpenID Connect client registration.
- .NET 8 SDK (or later).

## Step 1: Create a Console Project

```bash
dotnet new console -n VcHubWebApiDemo
cd VcHubWebApiDemo
```

## Step 2: C# Sample Code

Create or replace `Program.cs` with the following sample:

```csharp
using System.Net.Http.Headers;
using System.Net.Http.Json;

var baseUrl = "https://localhost:8043";
var clientId = "your_client_id";
var clientSecret = "your_client_secret";

using var httpHandler = new HttpClientHandler
{
    // For local development only. Use trusted certificates in production.
    ServerCertificateCustomValidationCallback = HttpClientHandler.DangerousAcceptAnyServerCertificateValidator
};
using var http = new HttpClient(httpHandler)
{
    BaseAddress = new Uri(baseUrl)
};

// 1) Discover token endpoint
var openIdConfigUrl = $"{baseUrl}/.well-known/openid-configuration";
var openIdDoc = await http.GetFromJsonAsync<OpenIdConfiguration>(openIdConfigUrl)
    ?? throw new InvalidOperationException("Failed to load OpenID metadata.");

if (string.IsNullOrWhiteSpace(openIdDoc.token_endpoint))
{
    throw new InvalidOperationException("token_endpoint is missing in OpenID metadata.");
}

// 2) Request access token (client credentials)
using var tokenResponse = await http.PostAsync(
    openIdDoc.token_endpoint,
    new FormUrlEncodedContent(new Dictionary<string, string>
    {
        ["client_id"] = clientId,
        ["client_secret"] = clientSecret,
        ["grant_type"] = "client_credentials"
    }));

tokenResponse.EnsureSuccessStatusCode();

var tokenPayload = await tokenResponse.Content.ReadFromJsonAsync<TokenResponse>()
    ?? throw new InvalidOperationException("Token response is empty.");

if (string.IsNullOrWhiteSpace(tokenPayload.access_token))
{
    throw new InvalidOperationException("access_token is missing in token response.");
}

// 3) Attach bearer token to all WebAPI calls
http.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", tokenPayload.access_token);

// 4) Example A: Query asset instances
var parentPath = Uri.EscapeDataString("Default");
using var getResponse = await http.GetAsync($"/api/v1/assetInstances?parentPath={parentPath}");
getResponse.EnsureSuccessStatusCode();

var getJson = await getResponse.Content.ReadAsStringAsync();
Console.WriteLine("GET /api/v1/assetInstances response:");
Console.WriteLine(getJson);

// 5) Example B: Create an asset instance
var createPayload = new
{
    parentPath = "Default",
    name = "demo_instance_from_openapi",
    modelPath = "Default:DemoModel"
};

using var postResponse = await http.PostAsJsonAsync("/api/v1/assetInstances", createPayload);
postResponse.EnsureSuccessStatusCode();

var postJson = await postResponse.Content.ReadAsStringAsync();
Console.WriteLine("POST /api/v1/assetInstances response:");
Console.WriteLine(string.IsNullOrWhiteSpace(postJson) ? "(empty body)" : postJson);

record OpenIdConfiguration(string token_endpoint);
record TokenResponse(string access_token, string token_type, int expires_in);
```

## Step 3: Run

```bash
dotnet run
```

If token and API permissions are correct, the console prints response payloads returned by the WebAPI endpoints.

## Troubleshooting

!!! warning
    If HTTPS certificate validation fails in development, trust your local certificate or use a valid CA-signed certificate in production. Avoid disabling certificate validation outside local testing.

!!! note
    If API returns `401 Unauthorized` or `403 Forbidden`, verify client credentials, token scope, and Open API permissions.

!!! tip
    You can verify the same endpoint and bearer token first in [Test with Postman](test-with-postman/index.md), then move confirmed values into C# code.

## Related Topics

- [Open Id Connect](open-id-connect.md)
- [Asset API Definitions](asset-api-definitions.md)
- [Test with Postman](test-with-postman/index.md)