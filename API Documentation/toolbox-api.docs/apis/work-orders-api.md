# Work Order Creation API

## Overview

The Work Order API allows maintenance systems to create and manage aircraft maintenance work orders.

A work order records maintenance tasks that must be performed on an aircraft.

---
## Endpoint
```
POST /workorders
```
---
## Description

Creates a new aircraft maintenance work order.

---
## Request Headers

|Header|Value|
|-----|------|
|Authorization|Bearer access_token|
|Content-Type|application/json|

---
## Request Body

|Field|Type|Required|Description|
|-----|----|---------|----------|
|aircraftId|string|Yes|Unique identifier for the aircraft|
|description|string|Yes|Maintenance task description|
|priority|string|Yes|Priority level (Low, Medium, High)|
|requestedBy|string|No|User creating the work order|

---
## Example Request
```
POST https://api.aircraft.com/v1/workorders
```
```
</> json
{
"aircraftId": "ZA123",
"description": "Replace hydraulic pump",
"priority": "High",
"requestedBy": "maintenance_engineer"
}
```
---
## Example Response
```
</> json
{
"workOrderId": "WO-12345",
"aircraftId": "ZA123",
"status": "Created",
"CreatedAt": "2026-04-08T11:30:20Z"
}
```
## Response Fields

|Field      |Type   |Description|
|---------- |-------|-----------|
|workOrderId|string |Unique identifier for the work order|
|aircraftId |string |Aircraft identifier|
|status     |string |Current status of the work order|
|CreatedAt  |string |Timestamp when the work order was created|
---
## Error Responses
|Status Code|Description|
|-----------|-----------|
|400|Invalid request body|
|401|Unauthorized request|
|403|User does not have permission|
|500|Internal server error|

---
