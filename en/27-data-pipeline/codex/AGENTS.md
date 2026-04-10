# Data Pipeline Harness

This folder is the Codex version of the Data Pipeline Harness. Start with the local `data-pipeline` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/data-pipeline/SKILL.md`
- Specialist agents: `.codex/agents/data-quality-manager.toml`, `.codex/agents/etl-architect.toml`, `.codex/agents/monitoring-specialist.toml`, `.codex/agents/pipeline-reviewer.toml`, `.codex/agents/scheduler-engineer.toml`
- Extension skills: `.agents/skills/dag-orchestration-patterns/SKILL.md`, `.agents/skills/data-quality-framework/SKILL.md`

## Workflow

- Start full-pipeline work with `data-pipeline`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness that collaborates to design and implement data pipelines covering ingestion, transformation, loading, quality verification, and monitoring.

## Deliverables

- `00_input.md` — Organized user input
- `01_etl_architecture.md` — ETL architecture design document
- `02_data_quality_plan.md` — Data quality management plan
- `03_scheduler_config.md` — Scheduling configuration and DAG definitions
- `04_monitoring_setup.md` — Monitoring dashboard and alert configuration
- `05_review_report.md` — Review report
- `pipeline_code/` — Pipeline implementation code
