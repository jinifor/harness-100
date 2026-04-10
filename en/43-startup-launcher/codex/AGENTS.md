# Startup Launcher Harness

This folder is the Codex version of the Startup Launcher Harness. Start with the local `startup-launcher` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/startup-launcher/SKILL.md`
- Specialist agents: `.codex/agents/business-modeler.toml`, `.codex/agents/launch-reviewer.toml`, `.codex/agents/market-analyst.toml`, `.codex/agents/mvp-architect.toml`, `.codex/agents/pitch-creator.toml`
- Extension skills: `.agents/skills/pitch-deck-framework/SKILL.md`, `.agents/skills/unit-economics-calculator/SKILL.md`

## Workflow

- Start full-pipeline work with `startup-launcher`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Startup launch planning: a harness where an agent team collaborates to perform market analysis → business modeling → MVP architecture → pitch deck creation → launch review.
