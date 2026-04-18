# Input:
API to pause scan POST /scan/{id}/pause 
returns scan status paused 
user can resume later 
if already paused return error 
api key required 
maybe timeout error also

### CLARIFICATION QUESTIONS:

- What is the exact response structure for a successful pause request (fields such as scan_id, status)?
- What error code and message should be returned if the scan is already paused?
- What does "timeout error" refer to? Is there a specific status code (e.g., 408 or 500)?
- Does this API require any request body, or is the scan ID sufficient?
- Should the response include only the status, or additional details?
- What is the expected success status value (e.g., "paused")?
- Is there a standard error response format to follow across APIs?

No response to the questions. 
---

### ASSUMPTIONS (CRUCIAL)

```
ASSUMPTIONS:
- Response includes only the scan status as "paused"
- Error codes and exact error structure are not defined, so only conditions are documented
- No request body is required as it is not specified in the input
```

# Pause Scan API
## Overview
This API pauses an active scan.

## Endpoint
POST /scan/{id}/pause
## Authentication
An API key is required.

Authorization: API-Key your_api_key_here

## Respose Example
```json
{
"status": "paused"
}
```
## Error handling
|Condition     |Description   |
|--------------|--------------|
|Already paused|Error returned|
|Timeout       |Timeout error |

## Notes
- A paused scan can be resumed later
