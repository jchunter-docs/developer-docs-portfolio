# Error handling

AstraCompute uses standard HTTP status codes and structured JSON error responses.

## Error response format

```json
{
  "error": {
    "code": "invalid_api_key",
    "message": "The API key is missing, invalid, or expired.",
    "request_id": "req_19cf02a7"
  }
}
```

## Common errors

| HTTP status | Code | Cause | Recommended action |
| --- | --- | --- | --- |
| 400 | `invalid_request` | The request body is missing a required field or uses an unsupported value. | Check the request schema and retry. |
| 401 | `invalid_api_key` | The API key is missing, invalid, or expired. | Generate a new key and update the `Authorization` header. |
| 403 | `model_access_denied` | Your account does not have access to the requested model. | Request access or choose an available model. |
| 404 | `model_not_found` | The requested model does not exist. | Verify the model ID. |
| 409 | `job_already_completed` | The job can no longer be canceled because it has completed. | Retrieve the job result instead. |
| 429 | `rate_limit_exceeded` | The request rate exceeded the account limit. | Retry after the delay shown in the `Retry-After` header. |
| 503 | `gpu_capacity_unavailable` | The selected GPU type is temporarily unavailable. | Retry later or choose a different GPU type. |

## Retry guidance

Retry only errors that are temporary or capacity-related.

Safe to retry:

- `rate_limit_exceeded`
- `gpu_capacity_unavailable`
- temporary network timeouts

Do not automatically retry:

- `invalid_api_key`
- `model_not_found`
- `model_access_denied`
- `invalid_request`

## Include request IDs in support requests

Every error response includes a `request_id`. Include this value when contacting support so the support team can find the relevant logs.

Example:

```text
Request ID: req_19cf02a7
```
