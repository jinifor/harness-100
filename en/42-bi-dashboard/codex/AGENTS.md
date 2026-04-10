# BI Dashboard Harness

This folder is the Codex version of the BI Dashboard Harness. Start with the local `bi-dashboard` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/bi-dashboard/SKILL.md`
- Specialist agents: `.codex/agents/bi-reviewer.toml`, `.codex/agents/dashboard-builder.toml`, `.codex/agents/data-engineer.toml`, `.codex/agents/kpi-designer.toml`, `.codex/agents/report-automator.toml`
- Extension skills: `.agents/skills/chart-selector/SKILL.md`, `.agents/skills/kpi-tree-builder/SKILL.md`

## Workflow

- Start full-pipeline work with `bi-dashboard`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- BI dashboard construction: a harness where an agent team collaborates to perform KPI design → data engineering → dashboard building → report automation → review.
