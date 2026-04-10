# Meal Planner Harness

This folder is the Codex version of the Meal Planner Harness. Start with the local `meal-planner` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/meal-planner/SKILL.md`
- Specialist agents: `.codex/agents/meal-designer.toml`, `.codex/agents/nutritionist.toml`, `.codex/agents/recipe-writer.toml`, `.codex/agents/shopping-coordinator.toml`
- Extension skills: `.agents/skills/ingredient-substitution-engine/SKILL.md`, `.agents/skills/nutrition-calculator/SKILL.md`

## Workflow

- Start full-pipeline work with `meal-planner`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A meal planning agent team harness.
