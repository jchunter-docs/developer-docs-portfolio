# Create a GPU inference job

This guide shows how to create an asynchronous GPU inference job, check its status, and retrieve the result.

Use asynchronous jobs for longer-running requests, batch input, or workloads that may take more than a few seconds to complete.

## Create the job

Send a `POST` request to `/v1/jobs`.

```bash
curl -X POST "https://api.astracompute.example.com/v1/jobs" \
  -H "Authorization: Bearer $ASTRA_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "astra-large",
    "gpu_type": "A100",
    "input": {
      "prompt": "Summarize the benefits of GPU cloud platforms for AI teams."
    },
    "max_output_tokens": 300
  }'
```

A successful request returns a job object.

```json
{
  "id": "job_4f73a8d2",
  "status": "queued",
  "model": "astra-large",
  "gpu_type": "A100",
  "created_at": "2026-07-28T15:02:11Z"
}
```

## Check job status

Use the job ID to check the current status.

```bash
curl "https://api.astracompute.example.com/v1/jobs/job_4f73a8d2" \
  -H "Authorization: Bearer $ASTRA_API_KEY"
```

The job can return one of the following statuses.

| Status | Description |
| --- | --- |
| `queued` | The job has been accepted and is waiting for GPU capacity. |
| `running` | The job is currently running on a GPU worker. |
| `completed` | The job finished successfully and results are available. |
| `failed` | The job did not complete. Review the error object for details. |
| `canceled` | The job was canceled before completion. |

## Retrieve the result

When the job status is `completed`, the response includes an output object.

```json
{
  "id": "job_4f73a8d2",
  "status": "completed",
  "output": {
    "text": "GPU cloud platforms help AI teams scale inference workloads without managing physical hardware."
  },
  "usage": {
    "gpu_seconds": 4.8,
    "input_tokens": 13,
    "output_tokens": 18
  }
}
```

## Cancel a job

Cancel a queued or running job with `DELETE /v1/jobs/{job_id}`.

```bash
curl -X DELETE "https://api.astracompute.example.com/v1/jobs/job_4f73a8d2" \
  -H "Authorization: Bearer $ASTRA_API_KEY"
```

## Troubleshooting

- If a job remains `queued` longer than expected, check your selected GPU type and region.
- If the response returns `gpu_capacity_unavailable`, retry with a different GPU type.
- If the response returns `invalid_model_parameters`, compare your request body with the API reference.
