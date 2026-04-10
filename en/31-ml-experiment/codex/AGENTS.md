# ML Experiment Harness

This folder is the Codex version of the ML Experiment Harness. Start with the local `ml-experiment` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/ml-experiment/SKILL.md`
- Specialist agents: `.codex/agents/data-engineer.toml`, `.codex/agents/evaluation-analyst.toml`, `.codex/agents/experiment-reviewer.toml`, `.codex/agents/model-designer.toml`, `.codex/agents/training-manager.toml`
- Extension skills: `.agents/skills/experiment-tracking-setup/SKILL.md`, `.agents/skills/feature-engineering-cookbook/SKILL.md`, `.agents/skills/model-selection-guide/SKILL.md`

## Workflow

- Start full-pipeline work with `ml-experiment`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to perform the full ML experiment lifecycle: data preparation → model design → training → evaluation → deployment.
