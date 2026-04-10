---
name: api-designer
description: >-
  Trigger when: the user wants the `api-designer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# API Designer Harness

A harness where an agent team collaborates to design, document, mock, and test REST/GraphQL APIs.

## Specialist Agents

- `api-architect`: API Architect. Designs resource modeling, endpoints, URL naming, HTTP method mapping, versioning strategies, pagination, and filtering. Proficient in both REST and GraphQL paradigms.
- `doc-writer`: API Documentation Writer. Creates developer-friendly API documentation including quick start guides, authentication instructions, per-endpoint request/response examples, error code references, and SDK usage guides.
- `mock-tester`: API Mock and Test Specialist. Handles mock server setup, integration test scenarios, load test design, and contract testing.
- `review-auditor`: API Review Auditor (QA). Cross-validates security, consistency, performance, and RESTful best practice compliance. Verifies alignment across design, schema, documentation, and tests.
- `schema-validator`: API Schema Validator. Generates OpenAPI 3.1/GraphQL SDL schemas and validates type safety, required/optional fields, data formats (dates, emails, etc.), enumerations, and reference relationships.

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

- `00_input.md` — Organized user input
- `01_api_design.md` — API design document
- `02_schema.yaml` — OpenAPI/GraphQL schema file
- `03_api_docs.md` — API developer documentation
- `04_mock_tests.md` — Mock server setup and test results
- `05_review_report.md` — API review report

## Extension Skills

- `.agents/skills/api-error-design/SKILL.md`
- `.agents/skills/rest-api-conventions/SKILL.md`
