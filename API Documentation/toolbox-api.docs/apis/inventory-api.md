# Inventory API

## Overview

The Inventory API allows applications to retrieve inventory information for aircraft parts stored in maintenance warehouses.

This API helps maintenance systems track part availability across different locations.

## Endpoint
GET /inventory

## Description
Returns inventory levels for aircraft parts.

## Query Parameters

|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|partNumber|string|No|Aircraft part number|
|warehouse|string|No|Warehouse location|

## Example Request

GET https://api.aircraft.com/v1/inventory?partNumber=HYD12345
---

## Request Headers
|Header|Value|
|------|-----|
|Authorization|Bearer access_token|
|Content-Type|application/json|
---
## Example Response

</> json
{

"partNumber": "HYD12345",

"warehouse": "Renton",

"Quantity": 55,

"lastUpdated": "2026-04-08T10:15:30Z"

}

## Response Fields
|Field|Type|Description|
|-----|----|-----------|
|partNumber|string|Aircraft part number|
|warehouse|string|Warehouse location|
|Quantity|integer|Available stock quantity|
|lastUpdated|string|Timestamp of last inventory update|

## Error Responses
|Status Code|Description|
|-----------|-----------|
|400|Invalid request parameters|
|401|Unauthorized request|
|404|Inventory record not found|
|500|Internal server error|

