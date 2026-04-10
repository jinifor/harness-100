---
name: data-pipeline
description: >-
  Trigger when: the user wants the `data-pipeline` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Data Pipeline Harness

An agent team harness that collaborates to design and implement data pipelines covering ingestion, transformation, loading, quality verification, and monitoring.

## Specialist Agents

- `data-quality-manager`: data  administrator. data profiling, verification rule , or more detection as, data  tracking countto pipeline before betweenof data reliability .
- `etl-architect`: ETL architecture architect. data  analysis, schema , count·transformation·-based pipeline  lower,  stack lower,  code creation.
- `monitoring-specialist`: monitoring specialist. pipeline execution metric, data  dashboard, alert , SLA tracking,   runbook to pipelineof  possible .
- `pipeline-reviewer`: pipeline reviewer(QA). ETL-plan-scheduling-monitoring betweenof   verificationlower, operations also evaluationlower, ··risk  to feedback provided.
- `scheduler-engineer`: scheduling engineer. DAG ,  of , retry strategy, resource ,  strategy countto pipelineof -based automatic execution .

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
- `01_etl_architecture.md` — ETL architecture design document
- `02_data_quality_plan.md` — Data quality management plan
- `03_scheduler_config.md` — Scheduling configuration and DAG definitions
- `04_monitoring_setup.md` — Monitoring dashboard and alert configuration
- `05_review_report.md` — Review report
- `pipeline_code/` — Pipeline implementation code

## Extension Skills

- `.agents/skills/dag-orchestration-patterns/SKILL.md`
- `.agents/skills/data-quality-framework/SKILL.md`
