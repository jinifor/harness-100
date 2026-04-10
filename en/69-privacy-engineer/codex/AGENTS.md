# Privacy Engineer Harness

This folder is the Codex version of the Privacy Engineer Harness. Start with the local `privacy-engineer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/privacy-engineer/SKILL.md`
- Specialist agents: `.codex/agents/consent-designer.toml`, `.codex/agents/pia-assessor.toml`, `.codex/agents/privacy-law-analyst.toml`, `.codex/agents/process-architect.toml`
- Extension skills: `.agents/skills/data-flow-mapper/SKILL.md`, `.agents/skills/gdpr-pipa-cross-reference/SKILL.md`

## Workflow

- Start full-pipeline work with `privacy-engineer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A privacy engineering agent team harness.
