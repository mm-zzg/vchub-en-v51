# Use C# to Invoke Realtime Data API (SignalR)

This page shows a simple C# example for connecting to VC Hub Realtime Data API by SignalR.

For complete sample code and project structure, visit:

- <https://github.com/mm-zzg/vc-hub-openapi-signalr-demo>

## Overview

The typical integration flow is:

1. Get OpenID Connect metadata from `/.well-known/openid-configuration`.
2. Read `token_endpoint` from the metadata response.
3. Request an access token by `client_credentials`.
4. Connect to SignalR endpoint `/ws/v1/realtimeData` with `access_token`.
5. Invoke hub target (for example `TagValues`) and read realtime updates.

## Prerequisites

- VC Hub Open API is enabled.
- You have `client_id` and `client_secret` from OpenID Connect client registration.
- .NET 8 SDK (or later).
- NuGet package: `Microsoft.AspNetCore.SignalR.Client`.

## Step 1: Create a Console Project

```bash
dotnet new console -n VcHubRealtimeDemo
cd VcHubRealtimeDemo
dotnet add package Microsoft.AspNetCore.SignalR.Client
```

## Step 2: C# Sample Code

Create or replace `Program.cs` with the following sample:

```csharp
using System.Net.Http.Json;
using System.Text.Json;
using Microsoft.AspNetCore.SignalR.Client;

var baseUrl = "https://localhost:8043";
var clientId = "your_client_id";
var clientSecret = "your_client_secret";

// Tag paths to subscribe
var tagPaths = new[]
{
    "Default:m1",
    "Default:m2",
    "Default:m3"
};

using var httpHandler = new HttpClientHandler
{
    // For local development only. Use trusted certificates in production.
    ServerCertificateCustomValidationCallback = HttpClientHandler.DangerousAcceptAnyServerCertificateValidator
};
using var http = new HttpClient(httpHandler);

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

// 3) Connect realtime endpoint
var hubUrl = $"{baseUrl}/ws/v1/realtimeData";
var connection = new HubConnectionBuilder()
    .WithUrl(hubUrl, options =>
    {
        options.AccessTokenProvider = () => Task.FromResult(tokenPayload.access_token)!;
        options.HttpMessageHandlerFactory = handler =>
        {
            if (handler is HttpClientHandler h)
            {
                // For local development only. Use trusted certificates in production.
                h.ServerCertificateCustomValidationCallback = HttpClientHandler.DangerousAcceptAnyServerCertificateValidator;
            }

            return handler;
        };
    })
    .WithAutomaticReconnect()
    .Build();

connection.Closed += error =>
{
    Console.WriteLine($"Connection closed: {error?.Message}");
    return Task.CompletedTask;
};

await connection.StartAsync();
Console.WriteLine("Connected to realtimeData hub.");

// 4) Stream tag values from target: TagValues
await foreach (var batch in connection.StreamAsync<List<TagValue>>("TagValues", tagPaths))
{
    foreach (var item in batch)
    {
        Console.WriteLine($"{item.path} = {item.value} ({item.quality}) @ {item.time:O}");
    }
}

record OpenIdConfiguration(string token_endpoint);

record TokenResponse(string access_token, string token_type, int expires_in);

record TagValue(string path, JsonElement value, DateTimeOffset time, string quality);
```

## Step 3: Run

```bash
dotnet run
```

If connection and invocation are successful, the console prints realtime values continuously.

## Troubleshooting

!!! warning
    If HTTPS certificate validation fails in development, trust your local certificate or use a valid CA-signed certificate in production. Avoid disabling certificate validation outside local testing.

!!! note
    If `TagValues` does not return data, verify tag paths first by REST API in [Realtime Data API Definitions](realtime-data-api-definitions.md).

!!! tip
    You can first verify token and endpoint behavior in Postman, then move the same values into C# code.

## Related Topics

- [Open Id Connect](open-id-connect.md)
- [Realtime Data API Definitions](realtime-data-api-definitions.md)
- [Test with Postman](test-with-postman/index.md)
