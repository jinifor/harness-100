# Technical Writer Harness

This folder is the Codex version of the Technical Writer Harness. Start with the local `technical-writer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/technical-writer/SKILL.md`
- Specialist agents: `.codex/agents/diagram-maker.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/info-architect.toml`, `.codex/agents/tech-reviewer.toml`, `.codex/agents/version-controller.toml`
- Extension skills: `.agents/skills/api-doc-standards/SKILL.md`, `.agents/skills/code-example-patterns/SKILL.md`, `.agents/skills/diagram-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `technical-writer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- technical document writing structuredesign→→diagram→review→versionmanagement A harness where an agent team collaborates to produce deliverables.
