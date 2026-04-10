# Database Architect Harness

This folder is the Codex version of the Database Architect Harness. Start with the local `database-architect` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/database-architect/SKILL.md`
- Specialist agents: `.codex/agents/data-modeler.toml`, `.codex/agents/integration-reviewer.toml`, `.codex/agents/migration-manager.toml`, `.codex/agents/performance-analyst.toml`, `.codex/agents/security-auditor.toml`
- Extension skills: `.agents/skills/normalization-patterns/SKILL.md`, `.agents/skills/query-optimization-catalog/SKILL.md`

## Workflow

- Start full-pipeline work with `database-architect`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to perform DB design from modeling through migration, indexing, and query optimization.

## Deliverables

- `00_input.md` — Organized user input
- `01_data_model.md` — Data model design document
- `02_migration.sql` — Migration SQL scripts
- `02_migration_plan.md` — Migration plan
- `03_performance.md` — Performance optimization report
- `04_security.md` — Security verification report
- `05_review_report.md` — Integration review report
