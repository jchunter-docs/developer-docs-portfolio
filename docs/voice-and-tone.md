# Voice and tone guide

This sample documentation uses a clear, direct, developer-focused voice.

## Principles

### Be precise

Use specific endpoint names, field names, and status values.

Preferred:

> Send a `POST` request to `/v1/jobs`.

Avoid:

> Hit the job API.

### Be concise

Keep instructions short and action-oriented.

Preferred:

> Set your API key as an environment variable.

Avoid:

> It is recommended that users consider setting the API key as an environment variable before making API calls.

### Explain why when it helps

Developers need enough context to make decisions.

Preferred:

> Use asynchronous jobs for longer-running requests, batch input, or workloads that may take more than a few seconds to complete.

### Avoid unnecessary marketing language

Documentation should help developers complete tasks and understand the product.

Preferred:

> The selected GPU type affects latency, availability, and cost.

Avoid:

> Our world-class GPU infrastructure unlocks limitless performance.

## Terminology

| Use | Avoid |
| --- | --- |
| API key | token credential |
| job | task instance |
| request body | payload blob |
| GPU type | accelerator flavor |
| retry | try again |

## Error messages

Good error documentation should include:

- What happened.
- Why it happened.
- How to recover.
- Whether the request is safe to retry.
