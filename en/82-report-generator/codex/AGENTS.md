# Report Generator Harness

This folder is the Codex version of the Report Generator Harness. Start with the local `report-generator` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/report-generator/SKILL.md`
- Specialist agents: `.codex/agents/analyst.toml`, `.codex/agents/data-collector.toml`, `.codex/agents/executive-summarizer.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/visualizer.toml`
- Extension skills: `.agents/skills/data-visualization-guide/SKILL.md`, `.agents/skills/kpi-dashboard-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `report-generator`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- work report datacollection→analysis→visualization→→summary A harness where an agent team collaborates to produce deliverables.
