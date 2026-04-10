---
name: api-client-generator
description: >-
  Trigger when: the user wants the `api-client-generator` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# API Client Generator Harness

API client SDK generation: a harness in which an agent team collaborates to perform spec parsing, type generation, client code development, testing, and usage documentation.

## Specialist Agents

- `doc-writer`: SDK documentation specialist. Writes README, quick start guides, API references, usage examples, changelogs, and migration guides.
- `sdk-developer`: SDK client developer. Develops production-grade SDKs including HTTP client wrappers, authentication handlers, pagination helpers, retry/circuit breaker logic, and error handling.
- `spec-parser`: API spec parser. Parses API specifications in OpenAPI (Swagger), GraphQL SDL, gRPC Proto, and other formats to systematically extract endpoints, models, authentication methods, and error codes.
- `test-engineer`: SDK test engineer. Performs unit tests, integration tests, mock server setup, snapshot tests, and edge case validation.
- `type-generator`: Type generation specialist. Transforms API schemas into the target language's type system. Generates request/response models, enums, union types, generics, and utility types.

## Workflow

1. Gather the request, constraints, and any existing source material.
2. Save the starting context in `_workspace/00_input.md` when that helps downstream handoff.
3. Run the specialists needed for the request scope, using numbered `_workspace/` artifacts as handoff points.
4. Run the reviewer or synthesizer role, if present, after prerequisite artifacts exist.
5. Report skipped phases, limitations, and reused inputs in the final result.

## Output Rules

- Keep the source `.claude` files untouched.
- Keep all harness deliverables in `_workspace/`.
- If existing files already satisfy a phase, reference or copy them into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Deliverables

- `00_input.md` — User input and API spec information
- `01_spec_analysis.md` — API spec analysis results
- `02_types/` — Generated type definition files
- `03_client/` — SDK client code
- `04_tests/` — Test code
- `05_docs/` — Usage documentation

## Extension Skills

- `.agents/skills/openapi-spec-patterns/SKILL.md`
- `.agents/skills/sdk-design-patterns/SKILL.md`
