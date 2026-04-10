# API Client Generator Harness

This folder is the Codex version of the API Client Generator Harness. Start with the local `api-client-generator` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/api-client-generator/SKILL.md`
- Specialist agents: `.codex/agents/doc-writer.toml`, `.codex/agents/sdk-developer.toml`, `.codex/agents/spec-parser.toml`, `.codex/agents/test-engineer.toml`, `.codex/agents/type-generator.toml`
- Extension skills: `.agents/skills/openapi-spec-patterns/SKILL.md`, `.agents/skills/sdk-design-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `api-client-generator`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- API client SDK generation: a harness in which an agent team collaborates to perform spec parsing, type generation, client code development, testing, and usage documentation.

## Deliverables

- `00_input.md` — User input and API spec information
- `01_spec_analysis.md` — API spec analysis results
- `02_types/` — Generated type definition files
- `03_client/` — SDK client code
- `04_tests/` — Test code
- `05_docs/` — Usage documentation
