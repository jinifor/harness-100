# API Designer Harness

This folder is the Codex version of the API Designer Harness. Start with the local `api-designer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/api-designer/SKILL.md`
- Specialist agents: `.codex/agents/api-architect.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/mock-tester.toml`, `.codex/agents/review-auditor.toml`, `.codex/agents/schema-validator.toml`
- Extension skills: `.agents/skills/api-error-design/SKILL.md`, `.agents/skills/rest-api-conventions/SKILL.md`

## Workflow

- Start full-pipeline work with `api-designer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to design, document, mock, and test REST/GraphQL APIs.

## Deliverables

- `00_input.md` — Organized user input
- `01_api_design.md` — API design document
- `02_schema.yaml` — OpenAPI/GraphQL schema file
- `03_api_docs.md` — API developer documentation
- `04_mock_tests.md` — Mock server setup and test results
- `05_review_report.md` — API review report
