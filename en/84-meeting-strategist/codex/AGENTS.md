# Meeting Strategist Harness

This folder is the Codex version of the Meeting Strategist Harness. Start with the local `meeting-strategist` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/meeting-strategist/SKILL.md`
- Specialist agents: `.codex/agents/agenda-architect.toml`, `.codex/agents/background-researcher.toml`, `.codex/agents/followup-planner.toml`, `.codex/agents/framework-designer.toml`, `.codex/agents/template-builder.toml`
- Extension skills: `.agents/skills/decision-frameworks/SKILL.md`, `.agents/skills/facilitation-techniques/SKILL.md`

## Workflow

- Start full-pipeline work with `meeting-strategist`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- meeting strategy document agenda itemstructuredesign→backgroundmaterialresearch→decision-makingframework→meetingrecordtemplate→ A harness where an agent team collaborates to produce deliverables.
