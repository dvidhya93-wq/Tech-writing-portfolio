> # Prompt 2
> Role: Act as a senior technical writer.
> 
> Task: Create complete API documentation from the input. 
>
> Structure:
> 
> - Title Overview (what this API does) 
>
> - Endpoint (method + URL)
> 
>  - Authentication
> 
>  - Request parameters (table)
> 
> - Request example
> 
> - Response example 
>
> - Error codes (table)
> 
> - Notes (edge cases, limits)
> 
> Constraints:
> 
> - Keep it concise
> 
> - Use developer-friendly language
> 
> - Use markdown for output
>
> - Use only the information provided in the input.
>
> - Do not include any additional information in all the sections.
>
> - Remove the sections if the required information is not available.
>
> - Do not invent any new information if it is not available in the input.



> Input: API to start scan POST /scan/start with target url and scan type returns scan id and status queued api key required

# AI-generetated API documetation

[scan-start-api-prompt-2.md](https://github.com/user-attachments/files/28415380/scan-start-api-prompt-2.md)
# Start Scan API

## Overview

Starts a scan against a specified target. Returns a scan ID and an initial queued status.

---

## Endpoint

```
POST /scan/start
```

---

## Authentication

An API key is required for all requests.

---

## Request Parameters

| Parameter    | Type   | Required | Description                    |
|--------------|--------|----------|--------------------------------|
| `target_url` | string | Yes      | The URL of the target to scan. |
| `scan_type`  | string | Yes      | The type of scan to run.       |

---

## Request Example

```http
POST /scan/start
Content-Type: application/json

{
  "target_url": "https://example.com",
  "scan_type": "full"
}
```

---

## Response Example

```json
{
  "scan_id": "abc123",
  "status": "queued"
}
```

| Field     | Type   | Description                             |
|-----------|--------|-----------------------------------------|
| `scan_id` | string | Unique identifier for the created scan. |
| `status`  | string | Initial scan status. Returns `queued`.  |

