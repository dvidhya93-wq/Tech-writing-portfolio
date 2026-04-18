# Input
1. API to start scan POST /scan/start with target url and scan type 
returns scan id and status queued api key required

2. API to get scan status GET /scan/{id} 
returns scan id and status and vulnerabilities list 
if not found 404 api key required

3. API to stop scan POST /scan/{id}/stop
returns status stopped 
if invalid id 400 if server error 500 api key required

# Scan Lifecycle API
## Overview
APIs to start, monitor and stop a scan.

## Authentication
An API key is required.

Authorization: API-Key your_api_key_here
---

## Start Scan
### Endpoint
POST /scan/start
### Request Example
```json
{
"target_url": "https://example.com",
"scan_type": "full"
}
```
### Response Example
```json
{
"scan_id": "1234",
"status": "queued"
}
```
### Notes
- Scan starts in a queued state

### Error Handling
|Error Code|Description  |
|----------|-------------|
|400       |Invalid input|
|401       |Unauthorized |
|500       |Server error |

## Get Scan Status
### Endpoint
GET /scan/{id}
### Response Example
```json
{
"scan_id": "1234",
"status": "completed",
"vulnerabilities": []
}
```
### Error Handling
|Error Code|Description|
|----------|-----------|
|404       |Not found  |

## Stop Scan
### Endpoint
POST /scan/{id}/stop
### Response Example
```json
{
"status": "stopped"
}
```
### Error Handling
|Error Code|Description  |
|----------|-------------|
|400       |Invalid ID   |
|500       |Server error |
