# Proposal Writer Harness

This folder is the Codex version of the Proposal Writer Harness. Start with the local `proposal-writer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/proposal-writer/SKILL.md`
- Specialist agents: `.codex/agents/client-analyst.toml`, `.codex/agents/differentiator.toml`, `.codex/agents/pricing-strategist.toml`, `.codex/agents/proposal-designer.toml`, `.codex/agents/solution-architect.toml`
- Extension skills: `.agents/skills/roi-calculator/SKILL.md`, `.agents/skills/win-theme-builder/SKILL.md`

## Workflow

- Start full-pipeline work with `proposal-writer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- proposal clientanalysis→solutiondesign→price→differentiation→specialistperson A harness where an agent team collaborates to produce deliverables.
