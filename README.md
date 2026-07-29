# Developer Documentation Portfolio Sample

This repository contains a self-directed developer documentation sample created by **John C. Hunter** to demonstrate developer documentation structure, Markdown writing, API quick starts, tutorials, concept documentation, reference documentation, and docs-as-code familiarity.

The sample uses a fictional GPU cloud and inference platform called **AstraCompute**. It is not client work and is not associated with any employer or real product.

## Purpose

This portfolio sample demonstrates the ability to:

- Organize developer documentation using a docs-as-code structure.
- Write task-oriented tutorials and quick starts for technical users.
- Explain API authentication, request/response workflows, and error handling.
- Create OpenAPI-style reference material.
- Separate documentation types using the Diátaxis framework.
- Maintain a consistent voice and tone across a small documentation set.

## Documentation set

| Documentation type | File | Purpose |
| --- | --- | --- |
| Quick start / tutorial | [`docs/tutorials/quickstart-run-first-inference.md`](docs/tutorials/quickstart-run-first-inference.md) | Helps a developer make a first successful inference request. |
| How-to guide | [`docs/how-to/create-gpu-inference-job.md`](docs/how-to/create-gpu-inference-job.md) | Shows how to create and monitor an inference job. |
| Concept guide | [`docs/concepts/gpu-inference-jobs.md`](docs/concepts/gpu-inference-jobs.md) | Explains how GPU inference jobs work at a platform level. |
| API reference | [`docs/reference/inference-api.md`](docs/reference/inference-api.md) | Documents fictional REST endpoints and sample responses. |
| Error reference | [`docs/reference/error-handling.md`](docs/reference/error-handling.md) | Explains common API errors and recovery steps. |
| OpenAPI sample | [`openapi/astra-inference-openapi.yaml`](openapi/astra-inference-openapi.yaml) | Provides a small OpenAPI 3.0 example for the fictional API. |
| Documentation model | [`docs/diataxis-map.md`](docs/diataxis-map.md) | Shows how the documentation set maps to Diátaxis. |
| Voice and tone | [`docs/voice-and-tone.md`](docs/voice-and-tone.md) | Defines the documentation style used across the sample. |

## Notes for reviewers

This repository is intentionally small. It is designed to show documentation judgment, structure, and writing quality rather than full product coverage.

The fictional product and API examples are used only to demonstrate documentation style and organization.
