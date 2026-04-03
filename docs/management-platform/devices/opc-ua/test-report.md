# Common OPC UA Server Test Report

We use the following common OPC UA Server and test the communication between it and the OPC UA driver in VC Hub.

## OPC UA Server

1. Prosys: v5.5.0-341
2. Softing: v1.46.0.7478
3. Matrikon: v1.9.0.8629

## Test Results

#### 1.Supports connectivity via secure connections

|          | Authentication | Secured Connection |
|----------|----------------|--------------------|
| Prosys   | Y              | Y                  |
| Softing  | Y              | Y                  |
| Matrikon | Y              | Y                  |

#### 2.VC Hub supports the following data types for OPC UA Server

|                       | Prosys | Softing | Matrikon |
|-----------------------|--------|---------|----------|
| Byte                  | R/W    | R/W     | R/W      |
| SByte                 | R/W    | R/W     | R/W      |
| Int16                 | R/W    | R/W     | R/W      |
| Int32                 | R/W    | R/W     | R/W      |
| Int64                 | R/W    | R/W     | R/W      |
| UInt16                | R/W    | R/W     | R/W      |
| UInt32                | R/W    | R/W     | R/W      |
| UInt64                | R/W    | R/W     | R/W      |
| Float                 | R/W    | R/W     | R/W      |
| Double                | R/W    | R/W     | R/W      |
| String                | R/W    | R/W     | R/W      |
| Boolean               | R/W    | R/W     | R/W      |
| DateTime              | R/W    | R/W     | R/W      |
| Guid                  | R      | R       | R        |
| ByteString            | R      | R       | R        |
| XmlElement            | R      | R       | R        |
| NodeId                | R      | R       | R        |
| ExpandedNodeId        | R      | R       | R        |
| StatusCode            | R      | R       | R        |
| QualifiedName         | R      | R       | R        |
| LocalizedText         | R      | R       | R        |
| ExtensionObject       | R      | R       | R        |
| DataValue             | R      | R       | R        |
| Variant               | R      | R       | R        |
| Number                | R/W    | R/W     | R/W      |
| Integer               | R/W    | R/W     | R/W      |
| UInteger              | R/W    | R/W     | R/W      |
| Enumeration           | R/W    | R/W     | R/W      |
| One-dimensional array | R/W    | R/W     | R/W      |


