# Fitness Program Harness

This folder is the Codex version of the Fitness Program Harness. Start with the local `fitness-program` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/fitness-program/SKILL.md`
- Specialist agents: `.codex/agents/exercise-guide.toml`, `.codex/agents/nutrition-linker.toml`, `.codex/agents/program-architect.toml`, `.codex/agents/template-builder.toml`
- Extension skills: `.agents/skills/exercise-biomechanics/SKILL.md`, `.agents/skills/periodization-engine/SKILL.md`

## Workflow

- Start full-pipeline work with `fitness-program`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A fitness program design agent team harness.
