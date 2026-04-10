# Onboarding System Harness

This folder is the Codex version of the Onboarding System Harness. Start with the local `onboarding-system` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/onboarding-system/SKILL.md`
- Specialist agents: `.codex/agents/experience-reviewer.toml`, `.codex/agents/mentor-matcher.toml`, `.codex/agents/milestone-tracker.toml`, `.codex/agents/onboarding-architect.toml`, `.codex/agents/training-builder.toml`
- Extension skills: `.agents/skills/buddy-program-guide/SKILL.md`, `.agents/skills/learning-path-design/SKILL.md`

## Workflow

- Start full-pipeline work with `onboarding-system`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- New hire onboarding: A harness where an agent team collaborates to generate everything from checklists to training, mentor assignments, and 30-60-90 day plans.
