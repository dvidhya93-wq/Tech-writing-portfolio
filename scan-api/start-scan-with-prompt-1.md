> # Prompt 1:

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
>Constraints:
> 
> - Keep it concise
> 
> - Use developer-friendly language
> 
> - Use markdown for output 

>Input: API to start scan POST /scan/start with target url and scan type returns scan id and status queued api key required


# AI-generetated API documetation
[scan-start-api-prompt-1.md](https://github.com/user-attachments/files/28415305/scan-start-api-prompt-1.md)

# Start Scan API

## Overview

Initiates a new security scan against a target URL. Returns a scan ID and initial queue status that you can use to poll for results.

---

## Endpoint

```
POST /scan/start
```

---

## Authentication

All requests require an API key passed in the request header.

```
X-API-Key: your_api_key_here
```

Requests without a valid API key return `401 Unauthorized`.

---

## Request Parameters

| Parameter    | Type     | Required | Description                                                        |
|--------------|----------|----------|--------------------------------------------------------------------|
| `target_url` | `string` | Yes      | Fully qualified URL to scan (e.g., `https://example.com`)         |
| `scan_type`  | `string` | Yes      | Type of scan to run. Accepted values: `full`, `quick`, `passive`  |

---

## Request Example

```bash
curl -X POST https://api.example.com/scan/start \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your_api_key_here" \
  -d '{
    "target_url": "https://example.com",
    "scan_type": "full"
  }'
```

---

## Response Example

**HTTP 200 OK**

```json
{
  "scan_id": "sc_a1b2c3d4e5f6",
  "status": "queued",
  "target_url": "https://example.com",
  "scan_type": "full",
  "created_at": "2026-05-30T08:00:00Z"
}
```

| Field        | Type     | Description                                                                 |
|--------------|----------|-----------------------------------------------------------------------------|
| `scan_id`    | `string` | Unique identifier for the scan. Use this to poll for status/results.        |
| `status`     | `string` | Initial state. Always `queued` on creation.                                 |
| `target_url` | `string` | The URL submitted for scanning.                                             |
| `scan_type`  | `string` | The scan type that was requested.                                           |
| `created_at` | `string` | ISO 8601 timestamp of when the scan was queued.                             |

---

## Error Codes

| HTTP Status | Error Code              | Description                                               |
|-------------|-------------------------|-----------------------------------------------------------|
| `400`       | `invalid_request`       | Missing or malformed `target_url` or `scan_type`.         |
| `401`       | `unauthorized`          | API key is missing, invalid, or revoked.                  |
| `422`       | `unsupported_scan_type` | The `scan_type` value is not one of the accepted options. |
| `429`       | `rate_limit_exceeded`   | Too many requests. Back off and retry after the indicated delay. |
| `500`       | `internal_error`        | Server-side failure. Retry with exponential backoff.      |

---

## Notes

- **Polling:** This endpoint only queues the scan. Use `GET /scan/{scan_id}/status` to check progress and retrieve results.
- **URL validation:** `target_url` must include the scheme (`https://` or `http://`). Bare domains (e.g., `example.com`) will return a `400` error.
- **Scan types:** Only `full`, `quick`, and `passive` are valid. Any other value returns `422`.
- **Rate limits:** Concurrent scan limits may apply depending on your plan tier. Check the `Retry-After` header on `429` responses.
- **Idempotency:** Submitting the same `target_url` and `scan_type` does not deduplicate — each request creates a new scan with a unique `scan_id`.
