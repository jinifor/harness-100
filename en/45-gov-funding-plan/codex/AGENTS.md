# Government Funding Plan Harness

This folder is the Codex version of the Government Funding Plan Harness. Start with the local `gov-funding-plan` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/gov-funding-plan/SKILL.md`
- Specialist agents: `.codex/agents/announcement-analyst.toml`, `.codex/agents/biz-writer.toml`, `.codex/agents/budget-planner.toml`, `.codex/agents/submission-reviewer.toml`, `.codex/agents/tech-writer.toml`
- Extension skills: `.agents/skills/budget-standard-checker/SKILL.md`, `.agents/skills/scoring-optimizer/SKILL.md`

## Workflow

- Start full-pipeline work with `gov-funding-plan`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Government funding proposal: a harness where an agent team collaborates to perform announcement analysis → business plan writing → technical writing → budget planning → submission review.
