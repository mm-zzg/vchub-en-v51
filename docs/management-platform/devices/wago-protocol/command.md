# WAGO Protocol `WriteValue` Command Configuration and Response Processing

## 1. Purpose

This document describes how to configure a `WriteValue` command with `WagoAppCloud` and provides a reference implementation for processing the command and generating a response.

A typical use case is:

> VC Hub / Cloud sends a WAGO Protocol write command to a WAGO PLC. The PLC locates the target variable by `Name`, writes the supplied `Value`, and returns the execution result.

> **Important: The code in this document is provided as a reference example only. For an actual implementation, use the official WAGO example project and WAGO documentation as the primary reference.**


## 2. Command Definition

| Item | Example Value | Description |
|---|---|---|
| Command ID | `0` | **User configurable.** `0` is only the value used in this example. The actual ID may be changed as long as it does not conflict with another registered Command ID |
| Command Name | `WriteValue` | **Must be exactly `WriteValue` for VC Hub back-write.** VC Hub internally uses this fixed command name; changing it will cause VC Hub back-write to fail |
| Number of Request Parameters | `3` | `Name`, `Value`, `RequestId` |
| Number of Response Parameters | `3` | `Name`, `Success`, `RequestId` |

### 2.1 About `aCommandDescriptions[0]`

In the expression:

```iecst
aCommandDescriptions[0]
```

`[0]` is only the **array subscript** of the IEC 61131-3 / Structured Text array `aCommandDescriptions`. It means that this example stores the command description in the first element of the array.

It is **not a WAGO Protocol Command configuration parameter**, and there is no separate protocol field that needs to be configured as `Command Index`. The previous `Command Index` row has therefore been removed from this document.

For example, an application with several commands may use:

```iecst
aCommandDescriptions[0]   // First command description
aCommandDescriptions[1]   // Second command description
aCommandDescriptions[2]   // Third command description
```

The array subscript does not have to equal `bCommandId`. For example, this is also a valid way to organize the PLC application:

```iecst
aCommandDescriptions[0].bCommandId := 10;
aCommandDescriptions[1].bCommandId := 20;
```

The protocol command is identified by `bCommandId` and the other properties of the command description, not by the PLC array subscript `[0]`.

### 2.2 Two Critical Requirements for VC Hub Back-Write

> **Command ID is configurable; Command Name is fixed to `WriteValue`.**

1. **The Command ID can be defined by the user.** The value `0` in this document is only an example. Any non-conflicting ID may be used.
2. **The Command Name must be `WriteValue`.** This is a VC Hub integration requirement, not a general restriction of the WAGO Protocol. VC Hub internally invokes the back-write command using the fixed name `WriteValue`; another name will cause the VC Hub back-write operation to fail.
3. If the Command ID is changed, the corresponding `CASE` branch in the command-processing code must be changed as well. For example, if the ID is changed to `10`:

```iecst
aCommandDescriptions[0].bCommandId := 10;
aCommandDescriptions[0].sName := 'WriteValue'; // Required by VC Hub back-write. Do not rename.
```

then the processing logic must use:

```iecst
CASE dwReceivedCmdId OF
    10:
        // Process WriteValue
END_CASE
```

### Configuration Code

```iecst
// Configure Command0 to accept three string parameters
// and reply with three string parameters.
aCommandDescriptions[0].bCommandId := 0; // Example only. The Command ID can be customized, but must be unique.
aCommandDescriptions[0].bNumberOfRequestParameters := 3;
aCommandDescriptions[0].bNumberOfResponseParameters := 3;
aCommandDescriptions[0].sName := 'WriteValue';

// Configure the parameter names and types that Command0 receives
aCommandDescriptions[0].aRequestParameters[0].sParameterName := 'Name';
aCommandDescriptions[0].aRequestParameters[0].eParameterType :=
    WagoAppCloud.eCommandParameterType.CPT_STRING;

aCommandDescriptions[0].aRequestParameters[1].sParameterName := 'Value';
aCommandDescriptions[0].aRequestParameters[1].eParameterType :=
    WagoAppCloud.eCommandParameterType.CPT_STRING;

aCommandDescriptions[0].aRequestParameters[2].sParameterName := 'RequestId';
aCommandDescriptions[0].aRequestParameters[2].eParameterType :=
    WagoAppCloud.eCommandParameterType.CPT_STRING;

// Configure the parameter names and types for Command0 response
aCommandDescriptions[0].aResponseParameters[0].sParameterName := 'Name';
aCommandDescriptions[0].aResponseParameters[0].eParameterType :=
    WagoAppCloud.eCommandParameterType.CPT_STRING;

aCommandDescriptions[0].aResponseParameters[1].sParameterName := 'Success';
aCommandDescriptions[0].aResponseParameters[1].eParameterType :=
    WagoAppCloud.eCommandParameterType.CPT_STRING;

aCommandDescriptions[0].aResponseParameters[2].sParameterName := 'RequestId';
aCommandDescriptions[0].aResponseParameters[2].eParameterType :=
    WagoAppCloud.eCommandParameterType.CPT_STRING;
```

## 3. Request Parameters

| Index | Parameter | Type | Description | Example |
|---:|---|---|---|---|
| `0` | `Name` | `CPT_STRING` | Name of the Tag / Point to be written | `TagA` |
| `1` | `Value` | `CPT_STRING` | New value to be written | `TRUE` |
| `2` | `RequestId` | `CPT_STRING` | Application-level request identifier | `REQ-0001` |

### Example Request

> `CommandId = 0` below is only an example. If another unique ID is configured, use that ID instead; `CommandName` must remain `WriteValue`.

```text
CommandId = 0
CommandName = WriteValue

Name      = TagA
Value     = TRUE
RequestId = REQ-0001
```

Although the actual PLC variable may be a `BOOL`, `INT`, `REAL`, or another type, all parameters in this example are defined as `STRING`. The PLC program therefore converts the received string to the target PLC data type.

For a BOOL variable:

```iecst
STRING_TO_BOOL(IncomingCommand.aRequestParameters[1].sParameterValue)
```

## 4. Response Parameters

| Index | Parameter | Type | Description | Example |
|---:|---|---|---|---|
| `0` | `Name` | `CPT_STRING` | Tag / Point associated with this write operation | `TagA` |
| `1` | `Success` | `CPT_STRING` | Indicates whether the write succeeded | `TRUE` / `FALSE` |
| `2` | `RequestId` | `CPT_STRING` | The same application-level request ID received in the request | `REQ-0001` |

Successful response:

```text
Name      = TagA
Success   = TRUE
RequestId = REQ-0001
```

Failed response:

```text
Name      = TagA
Success   = FALSE
RequestId = REQ-0001
```

## 5. Response Processing Reference Code

> The `CASE ... 0:` branch below corresponds to the example `bCommandId := 0`. If the Command ID is changed, this CASE value must be changed to the same ID.
>
> The generic example also assumes that the project provides `dwConfiguredTagCount` (the actual number of configured writable Tags) and declares typed pointers for the supported destination types, such as `POINTER TO BOOL`, `POINTER TO INT`, and `POINTER TO REAL`. Adapt the Tag array name, collection count field, and pointer-casting syntax to the actual project and WagoAppCloud version.

```iecst
IF xCommandReceived THEN //After receiving the Command, xCommandReceived becomes True.
    dwReceivedCmdId := IncomingCommand.dwCommandId; //Obtain CommandId

    CASE dwReceivedCmdId OF //Determine CommandId
        0:
            response.dwCommandId := dwReceivedCmdId;
            //The response CommandId should be consistent with the received CommandId.

            response.bNumberOfResponseParameters := 3;
            //Set the number of response parameters to 3.

            response.dwInvokeId := IncomingCommand.dwInvokeId;
            //Keep the response invocation ID consistent with the request.

            //Set three response parameter types
            response.aResponseParameters[0].eParameterType :=
                aCommandDescriptions[0].aResponseParameters[0].eParameterType;

            response.aResponseParameters[1].eParameterType :=
                aCommandDescriptions[0].aResponseParameters[1].eParameterType;

            response.aResponseParameters[2].eParameterType :=
                aCommandDescriptions[0].aResponseParameters[2].eParameterType;

            //Set three response parameter names
            response.aResponseParameters[0].sParameterName :=
                aCommandDescriptions[0].aResponseParameters[0].sParameterName;

            response.aResponseParameters[1].sParameterName :=
                aCommandDescriptions[0].aResponseParameters[1].sParameterName;

            response.aResponseParameters[2].sParameterName :=
                aCommandDescriptions[0].aResponseParameters[2].sParameterName;

            //Set default values for the three response parameters
            response.aResponseParameters[0].sParameterValue :=
                IncomingCommand.aRequestParameters[0].sParameterValue;
            //Request and response tag names should be kept consistent.

            response.aResponseParameters[1].sParameterValue :=
                BOOL_TO_STRING(FALSE);
            //Default state: Command execution failed.

            response.aResponseParameters[2].sParameterValue :=
                IncomingCommand.aRequestParameters[2].sParameterValue;
            //The RequestId in the response must be consistent with the request.

            // IMPORTANT:
            // Do NOT hard-code 0..9. The effective search range must follow the
            // actual number of configured writable Tags in the project.
            // dwConfiguredTagCount should come from the actual collection/tag
            // configuration used by the project.

            iFirstIndex := LOWER_BOUND(Publish.aTagConfiguration0, 1);

            IF dwConfiguredTagCount > 0 THEN
                iLastIndex := iFirstIndex + DWORD_TO_INT(dwConfiguredTagCount) - 1;

                // Defensive check: never exceed the declared array boundary.
                IF iLastIndex > UPPER_BOUND(Publish.aTagConfiguration0, 1) THEN
                    iLastIndex := UPPER_BOUND(Publish.aTagConfiguration0, 1);
                END_IF

                FOR index := iFirstIndex TO iLastIndex DO
                    IF (
                        Publish.aTagConfiguration0[index].sTag =
                        IncomingCommand.aRequestParameters[0].sParameterValue
                    ) THEN
                        xTagFound := TRUE;
                        xWriteSuccess := FALSE;

                        // "Value" is transported by VC Hub as CPT_STRING.
                        // The destination type is determined by the matched Tag's
                        // eValueType, NOT by the Command parameter type.
                        CASE Publish.aTagConfiguration0[index].eValueType OF

                            WagoAppCloud.VVT_BOOL:
                                pBoolValue := Publish.aTagConfiguration0[index].pAddress;
                                pBoolValue^ := STRING_TO_BOOL(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_BYTE:
                                pByteValue := Publish.aTagConfiguration0[index].pAddress;
                                pByteValue^ := STRING_TO_BYTE(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_SINT:
                                pSintValue := Publish.aTagConfiguration0[index].pAddress;
                                pSintValue^ := STRING_TO_SINT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_USINT:
                                pUsintValue := Publish.aTagConfiguration0[index].pAddress;
                                pUsintValue^ := STRING_TO_USINT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_INT:
                                pIntValue := Publish.aTagConfiguration0[index].pAddress;
                                pIntValue^ := STRING_TO_INT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_UINT:
                                pUintValue := Publish.aTagConfiguration0[index].pAddress;
                                pUintValue^ := STRING_TO_UINT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_WORD:
                                pWordValue := Publish.aTagConfiguration0[index].pAddress;
                                pWordValue^ := STRING_TO_WORD(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_DINT:
                                pDintValue := Publish.aTagConfiguration0[index].pAddress;
                                pDintValue^ := STRING_TO_DINT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_UDINT:
                                pUdintValue := Publish.aTagConfiguration0[index].pAddress;
                                pUdintValue^ := STRING_TO_UDINT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_DWORD:
                                pDwordValue := Publish.aTagConfiguration0[index].pAddress;
                                pDwordValue^ := STRING_TO_DWORD(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_LINT:
                                pLintValue := Publish.aTagConfiguration0[index].pAddress;
                                pLintValue^ := STRING_TO_LINT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_ULINT:
                                pUlintValue := Publish.aTagConfiguration0[index].pAddress;
                                pUlintValue^ := STRING_TO_ULINT(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_LWORD:
                                pLwordValue := Publish.aTagConfiguration0[index].pAddress;
                                pLwordValue^ := STRING_TO_LWORD(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_REAL:
                                pRealValue := Publish.aTagConfiguration0[index].pAddress;
                                pRealValue^ := STRING_TO_REAL(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_LREAL:
                                pLrealValue := Publish.aTagConfiguration0[index].pAddress;
                                pLrealValue^ := STRING_TO_LREAL(IncomingCommand.aRequestParameters[1].sParameterValue);
                                xWriteSuccess := TRUE;

                            WagoAppCloud.VVT_STRING:
                                pStringValue := Publish.aTagConfiguration0[index].pAddress;
                                pStringValue^ := IncomingCommand.aRequestParameters[1].sParameterValue;
                                xWriteSuccess := TRUE;

                            ELSE
                                // Unsupported or unhandled Tag type.
                                xWriteSuccess := FALSE;
                        END_CASE

                        response.aResponseParameters[1].sParameterValue :=
                            BOOL_TO_STRING(xWriteSuccess);

                        EXIT;
                    END_IF
                END_FOR
            END_IF

            xResponseTrigger := TRUE;
            //Trigger the Command response.

    END_CASE
END_IF
```

---

## 6. Response Processing Logic

| Step | Code / Variable | Purpose |
|---:|---|---|
| 1 | `IF xCommandReceived THEN` | Checks whether a new Command has been received |
| 2 | `IncomingCommand.dwCommandId` | Reads the received Command ID |
| 3 | `CASE dwReceivedCmdId OF` | Selects the processing logic for the Command ID |
| 4 | `response.dwCommandId` | Sets the Command ID of the response |
| 5 | `response.dwInvokeId` | Preserves the Invoke ID for protocol-level request/response correlation |
| 6 | `eParameterType` | Copies the configured response parameter types |
| 7 | `sParameterName` | Copies the configured response parameter names |
| 8 | `Name` | Returns the requested Tag name |
| 9 | `Success` | Defaults to `FALSE` |
| 10 | `RequestId` | Returns the original application-level RequestId |
| 11 | `dwConfiguredTagCount` + array bounds | Derives the effective search range from the actual number of configured Tags; do not hard-code `0..9` |
| 12 | `sTag = Name` | Finds the target Tag by the requested `Name` |
| 13 | `eValueType` | Reads the actual WagoAppCloud data type of the matched Tag |
| 14 | `CASE ... eValueType OF` | Selects the corresponding `STRING_TO_*` conversion |
| 15 | `pAddress` + typed pointer | Writes the converted value to the actual PLC variable represented by the Tag |
| 16 | `Success` | Returns `TRUE` only when the type is supported and the write succeeds |
| 17 | `xResponseTrigger := TRUE` | Triggers sending of the response |


## 7. Difference Between `CommandId`, `InvokeId`, and `RequestId`

These identifiers serve different purposes.

| ID | Source | Purpose |
|---|---|---|
| `CommandId` | Command configuration | Identifies which command should be executed, e.g. `0 = WriteValue` |
| `InvokeId` | WagoAppCloud / protocol layer | Correlates a protocol command invocation with its response |
| `RequestId` | Application request parameter | Application-level identifier defined by VC Hub / the calling application |

Conceptually:

```text
CommandId
    ↓
“Which operation should be executed?”

InvokeId
    ↓
“Which protocol invocation does this response belong to?”

RequestId
    ↓
“Which business-level write request does this belong to?”
```


## 8. Example Execution Flow

VC Hub sends:

```text
CommandId = 0
Name      = TagA
Value     = TRUE
RequestId = REQ-0001
```

PLC processing:

```text
xCommandReceived = TRUE
        ↓
Read CommandId
        ↓
CommandId = 0
        ↓
Enter WriteValue handling
        ↓
Search Publish.aTagConfiguration0[*].sTag
        ↓
Find TagA
        ↓
Read TagA.eValueType
        ↓
Select the matching STRING_TO_* conversion
        ↓
Write through the Tag's pAddress to the actual PLC variable
        ↓
Write succeeds → Success := TRUE
        ↓
xResponseTrigger := TRUE
```

Response:

```text
Name      = TagA
Success   = TRUE
RequestId = REQ-0001
```


## 9. Implementation Notes

### 9.1 `Name` Must Already Be Assigned

The reference snippet contains:

```iecst
IF (Publish.aTagConfiguration0[index].sTag = Name) THEN
```

but the provided code fragment does not show where `Name` is assigned.

Before entering the loop, ensure that `Name` contains the first request parameter, for example:

```iecst
Name := IncomingCommand.aRequestParameters[0].sParameterValue;
```

Alternatively, compare directly:

```iecst
IF (
    Publish.aTagConfiguration0[index].sTag =
    IncomingCommand.aRequestParameters[0].sParameterValue
) THEN
```

The complete official example project should be treated as the reference for the actual implementation.

### 9.2 The Tag Search Range Must Follow the Actual Configuration

The following is only valid for a demo with exactly ten Tags at indexes 0..9:

```iecst
FOR index := 0 TO 9 DO
```

A production implementation must derive the effective range from the **actual number of configured writable Tags**.

Recommended rules:

- If the Tag array length exactly equals the number of configured Tags, `LOWER_BOUND()` / `UPPER_BOUND()` can be used directly.
- If the array is only a capacity buffer and some elements are unused, use the actual configured count from the collection/tag configuration, or a project-maintained `dwConfiguredTagCount`.
- Even when using a count, clamp the calculated last index with `UPPER_BOUND()` defensively.
- If sparse Tag indexes are allowed, scan the legal array range and skip empty/disabled entries instead of assuming contiguous indexes.

Here, “dynamic range” means **calculating the effective search range from the actual configuration**, not assuming that the IEC array itself is dynamically allocated at runtime.

### 9.3 `Value` Is Received as STRING, but the Target PLC Type Comes from the Tag Configuration

For the VC Hub `WriteValue` contract, the Command parameter type of request parameter `Value` must remain:

```text
CPT_STRING
```

The PLC therefore receives the value as text.

However, **the Command parameter type must not determine the final PLC destination type**, because it is fixed as `CPT_STRING`. The conversion target must come from the matched Tag configuration, for example:

```iecst
Publish.aTagConfiguration0[index].eValueType
```

Correct logic:

```text
Name
 ↓
Find matching Tag
 ↓
Read Tag.eValueType
 ↓
BOOL   → STRING_TO_BOOL
INT    → STRING_TO_INT
DINT   → STRING_TO_DINT
REAL   → STRING_TO_REAL
STRING → direct assignment
...    → handle every type supported by the installed WagoAppCloud version
```

Newer WAGO firmware Release Notes explicitly state that WagoAppCloud added support for `SINT`, `LINT`, `ULINT`, and `LWORD`, so a generic implementation must not stop at older BOOL/INT/REAL examples.

Official Release Notes:

https://downloadcenter.wago.com/api/uploads/2026_03_11_Release_Notes_750_8x1x_7373429583.pdf

> **Version note:** The set of `VVT_*` values can vary by WagoAppCloud version. The final implementation must inspect the `eValueType` / `VVT_*` definitions in the WagoAppCloud library actually installed in the project and add a matching `CASE` branch for every writable type supported by that version.

### 9.4 Generic Type Conversion Mapping

| Tag `eValueType` | String conversion | Target PLC type |
|---|---|---|
| `VVT_BOOL` | `STRING_TO_BOOL` | `BOOL` |
| `VVT_BYTE` | `STRING_TO_BYTE` | `BYTE` |
| `VVT_SINT` | `STRING_TO_SINT` | `SINT` |
| `VVT_USINT` | `STRING_TO_USINT` | `USINT` |
| `VVT_INT` | `STRING_TO_INT` | `INT` |
| `VVT_UINT` | `STRING_TO_UINT` | `UINT` |
| `VVT_WORD` | `STRING_TO_WORD` | `WORD` |
| `VVT_DINT` | `STRING_TO_DINT` | `DINT` |
| `VVT_UDINT` | `STRING_TO_UDINT` | `UDINT` |
| `VVT_DWORD` | `STRING_TO_DWORD` | `DWORD` |
| `VVT_LINT` | `STRING_TO_LINT` | `LINT` |
| `VVT_ULINT` | `STRING_TO_ULINT` | `ULINT` |
| `VVT_LWORD` | `STRING_TO_LWORD` | `LWORD` |
| `VVT_REAL` | `STRING_TO_REAL` | `REAL` |
| `VVT_LREAL` | `STRING_TO_LREAL` | `LREAL` |
| `VVT_STRING` | Direct assignment | `STRING` |

If the installed library defines additional writable `VVT_*` values, add corresponding branches. Unknown types should fail rather than being forced through an arbitrary conversion.

### 9.5 Conversion Failure Must Also Produce a Failed Response

Type matching alone is not enough. The incoming text must be valid and within the destination type's range. For example, `Value = "ABC"` for an `INT`, or a number far outside the `INT` range, must not result in `Success = TRUE`.

Production code should validate format and range. Success should only be returned when the Tag exists, the type is supported, the value is valid, and the write completes.

### 9.6 `Success` Is Defined as STRING

Although `Success` logically represents a Boolean result, the command description defines it as:

```text
CPT_STRING
```

The sample therefore returns:

```iecst
BOOL_TO_STRING(TRUE)
BOOL_TO_STRING(FALSE)
```

### 9.7 Restrict Remote-Writable Variables

For production use, only explicitly approved PLC variables should be writable remotely. A whitelist of allowed Tags is preferable to exposing arbitrary PLC variables through the `Name` parameter.


## 10. Overall Flow

```text
VC Hub / Cloud
      |
      | WriteValue
      | CommandId = 0
      | Name = TagA
      | Value = TRUE
      | RequestId = REQ-0001
      v
+---------------------------+
|         WAGO PLC          |
|                           |
| FbCommandListener         |
|          |                |
|          v                |
| IncomingCommand           |
|          |                |
|          v                |
| Check CommandId           |
|          |                |
|          v                |
| Find PLC Tag by Name      |
|          |                |
|          v                |
| Convert STRING -> Tag Type|
|          |                |
|          v                |
| Write PLC Variable        |
|          |                |
|          v                |
| Build response            |
|          |                |
|          v                |
| xResponseTrigger = TRUE   |
|          |                |
|          v                |
| FbCommandResponder        |
+---------------------------+
      |
      | Name = TagA
      | Success = TRUE
      | RequestId = REQ-0001
      v
VC Hub / Cloud
```


## 11. Official References

> **The code above is only a reference example. The WAGO official sample project and documentation should be used as the authoritative implementation reference.**
>
> In the Command Handling section of the WagoAppCloud Application Note, WAGO describes command registration through `FbCommandConfigurator` using `typCommandDescription`; incoming requests are provided through `typCommandRequest`, and responses through `typCommandResponse`. The documentation does not define a protocol parameter named `Command Index`. Therefore, `[0]` in `aCommandDescriptions[0]` is an application-level array subscript, not a WAGO Protocol field.

### 11.1 `WagoAppCloud_FbCommandListener_Example_01`

WAGO Download Center:

https://downloadcenter.wago.com/wago/learning-material/details/lh0jtfwxwco4wt7ifle

Refer in particular to:

```text
WagoAppCloud_FbCommandListener_Example_01
```

The example demonstrates how `FbCommandListener`, Command Description, Command Request, Command Response, and `FbCommandResponder` work together.

### 11.2 Cloud Connectivity / WagoAppCloud Documentation

Current WAGO Cloud Connectivity page:

https://www.wago.com/global/trends-topics-technologies/topics/open-automation/cloud-connectivity

Official Application Note entry linked from the current WAGO page:

https://www.wago.com/global/d/15719

Because WAGO may update packages or change direct download URLs, obtain the newest revision through the official Cloud Connectivity page or WAGO Download Center whenever possible.
