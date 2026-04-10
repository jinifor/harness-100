---
name: bi-dashboard
description: >-
  Trigger when: the user wants the `bi-dashboard` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# BI Dashboard Harness

BI dashboard construction: a harness where an agent team collaborates to perform KPI design → data engineering → dashboard building → report automation → review.

## Specialist Agents

- `bi-reviewer`: BI reviewer (QA). Cross-validates consistency between data model, KPI calculations, visualizations, and reports. Identifies data errors, metric contradictions, and UX issues to provide feedback.
- `dashboard-builder`: Dashboard builder. Designs dashboard layouts, chart types, interactions, and color schemes that effectively visualize KPIs.
- `data-engineer`: BI data engineer. Performs source data analysis, data warehouse schema design, ETL pipeline definition, and data quality rule establishment.
- `kpi-designer`: KPI designer. Derives key performance indicators from business objectives and defines calculation logic, targets, benchmarks, and drill-down paths.
- `report-automator`: Report automation specialist. Builds scheduled report generation, alert rule configuration, distribution channel management, and data storytelling templates.

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

## Extension Skills

- `.agents/skills/chart-selector/SKILL.md`
- `.agents/skills/kpi-tree-builder/SKILL.md`
