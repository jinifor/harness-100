# Side Project Launcher Harness

This folder is the Codex version of the Side Project Launcher Harness. Start with the local `side-project-launcher` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/side-project-launcher/SKILL.md`
- Specialist agents: `.codex/agents/idea-validator.toml`, `.codex/agents/launch-reviewer.toml`, `.codex/agents/mvp-designer.toml`, `.codex/agents/roadmap-builder.toml`, `.codex/agents/techstack-analyst.toml`
- Extension skills: `.agents/skills/market-sizing-calculator/SKILL.md`, `.agents/skills/techstack-decision-matrix/SKILL.md`

## Workflow

- Start full-pipeline work with `side-project-launcher`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- companyproject basis ideaverify→tech stack→MVP→developmentroadmap→launchchecklist A harness where an agent team collaborates to produce deliverables.
