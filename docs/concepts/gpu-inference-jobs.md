# GPU inference jobs

A GPU inference job is a request to run a trained model on GPU-backed infrastructure and return a prediction, generation, embedding, or classification result.

AstraCompute supports two inference patterns:

- **Synchronous inference** for short requests that return immediately.
- **Asynchronous jobs** for longer-running workloads that need queueing, status checks, or batch processing.

## How a job moves through the system

A typical asynchronous job moves through the following stages:

1. **Accepted** — The API validates the request and creates a job record.
2. **Queued** — The scheduler waits for available GPU capacity.
3. **Running** — A GPU worker loads the model and processes the input.
4. **Completed** — The platform stores the result and makes it available through the API.
5. **Expired** — Results are removed after the retention period.

## When to use asynchronous jobs

Use asynchronous jobs when:

- The request may take longer than a synchronous HTTP timeout.
- You need to process multiple inputs.
- You want to track progress or retry failures.
- You want to select a specific GPU type or region.

Use synchronous inference when:

- The request is small.
- You need a response immediately.
- The model and input size are predictable.

## GPU type selection

The selected GPU type affects latency, availability, and cost. Larger GPUs can process more demanding workloads, but they may have longer queue times or higher usage charges.

| GPU type | Best for |
| --- | --- |
| `T4` | Small models, development, and low-cost testing. |
| `L4` | General-purpose inference and balanced cost/performance. |
| `A100` | Large models, high-throughput workloads, and production inference. |

## Reliability considerations

Production workloads should include:

- Retry logic for rate limits and temporary capacity errors.
- Request IDs for support and troubleshooting.
- Timeouts appropriate for the expected workload.
- Monitoring for failed jobs and unusual queue times.
- Clear user messaging when a job is delayed or canceled.

## Related documentation

- [Quick start: Run your first inference request](../tutorials/quickstart-run-first-inference.md)
- [Create a GPU inference job](../how-to/create-gpu-inference-job.md)
- [Error handling](../reference/error-handling.md)
