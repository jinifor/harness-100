# Data Analysis Harness

This folder is the Codex version of the Data Analysis Harness. Start with the local `data-analysis` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/data-analysis/SKILL.md`
- Specialist agents: `.codex/agents/analyst.toml`, `.codex/agents/cleaner.toml`, `.codex/agents/explorer.toml`, `.codex/agents/reporter.toml`, `.codex/agents/visualizer.toml`
- Extension skills: `.agents/skills/statistical-tests-selector/SKILL.md`, `.agents/skills/visualization-chooser/SKILL.md`

## Workflow

- Start full-pipeline work with `data-analysis`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to perform the full data analysis lifecycle: exploration → cleaning → analysis → visualization → reporting.
