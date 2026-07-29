# Quick start: Run your first inference request

This quick start shows how to submit a text prompt to the fictional AstraCompute Inference API and retrieve a model response.

## What you'll do

In this tutorial, you will:

1. Create an API key.
2. Send a request to the `/v1/inference` endpoint.
3. Review the response.
4. Troubleshoot common first-request errors.

## Before you begin

You need:

- An AstraCompute account.
- An active API key.
- `curl` installed on your machine.
- Basic familiarity with REST APIs and JSON.

## 1. Set your API key

Set your API key as an environment variable so you do not need to paste it directly into each request.

```bash
export ASTRA_API_KEY="replace-with-your-api-key"
```

On Windows PowerShell, use:

```powershell
$env:ASTRA_API_KEY="replace-with-your-api-key"
```

## 2. Send an inference request

Use the following request to send a prompt to the model:

```bash
curl -X POST "https://api.astracompute.example.com/v1/inference" \
  -H "Authorization: Bearer $ASTRA_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "astra-small",
    "input": {
      "prompt": "Explain GPU inference in one sentence."
    },
    "max_output_tokens": 100
  }'
```

## 3. Review the response

A successful response returns an inference ID, status, and generated output.

```json
{
  "id": "inf_8a82c91f",
  "status": "completed",
  "model": "astra-small",
  "output": {
    "text": "GPU inference uses graphics processors to run trained AI models quickly and efficiently."
  },
  "usage": {
    "input_tokens": 9,
    "output_tokens": 15
  }
}
```

## 4. Handle common errors

If your request fails, check the HTTP status code and the `code` value in the error response.

| Status | Error code | What it means | How to fix it |
| --- | --- | --- | --- |
| 401 | `invalid_api_key` | The API key is missing or invalid. | Confirm the key is active and included in the `Authorization` header. |
| 404 | `model_not_found` | The requested model is unavailable. | Verify the model name or choose another model. |
| 429 | `rate_limit_exceeded` | Too many requests were sent. | Retry after the time shown in the `Retry-After` header. |

## Next steps

- Learn how inference jobs work in [GPU inference jobs](../concepts/gpu-inference-jobs.md).
- Create a longer-running job in [Create a GPU inference job](../how-to/create-gpu-inference-job.md).
- Review available endpoints in [Inference API reference](../reference/inference-api.md).
