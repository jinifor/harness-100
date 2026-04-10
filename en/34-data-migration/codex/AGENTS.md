# Data Migration Harness

This folder is the Codex version of the Data Migration Harness. Start with the local `data-migration` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/data-migration/SKILL.md`
- Specialist agents: `.codex/agents/rollback-planner.toml`, `.codex/agents/schema-mapper.toml`, `.codex/agents/script-developer.toml`, `.codex/agents/source-analyst.toml`, `.codex/agents/validation-engineer.toml`
- Extension skills: `.agents/skills/data-validation-patterns/SKILL.md`, `.agents/skills/type-mapping-encyclopedia/SKILL.md`

## Workflow

- Start full-pipeline work with `data-migration`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Data migration: a harness in which an agent team collaborates to perform source analysis, schema mapping, transformation script generation, validation queries, and rollback planning.

## Deliverables

- `00_input.md` — User input and migration requirements
- `01_source_analysis.md` — Source system analysis report
- `02_schema_mapping.md` — Schema mapping specification
- `03_migration_scripts/` — Transformation scripts directory
- `04_validation_suite.md` — Validation queries and test suite
- `05_rollback_plan.md` — Rollback and emergency response plan
