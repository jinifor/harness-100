# Event Organizer Harness

This folder is the Codex version of the Event Organizer Harness. Start with the local `event-organizer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/event-organizer/SKILL.md`
- Specialist agents: `.codex/agents/concept-planner.toml`, `.codex/agents/evaluation-analyst.toml`, `.codex/agents/logistics-manager.toml`, `.codex/agents/program-designer.toml`, `.codex/agents/promotion-lead.toml`
- Extension skills: `.agents/skills/budget-planning/SKILL.md`, `.agents/skills/venue-evaluation/SKILL.md`

## Workflow

- Start full-pipeline work with `event-organizer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- event basis·operations: concept→venue→program→promotion→execution→companyafterassessmentto A harness where an agent team collaborates to produce deliverables.
