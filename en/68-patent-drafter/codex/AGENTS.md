# Patent Drafter Harness

This folder is the Codex version of the Patent Drafter Harness. Start with the local `patent-drafter` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/patent-drafter/SKILL.md`
- Specialist agents: `.codex/agents/claim-drafter.toml`, `.codex/agents/drawing-designer.toml`, `.codex/agents/patent-reviewer.toml`, `.codex/agents/prior-art-researcher.toml`, `.codex/agents/specification-writer.toml`
- Extension skills: `.agents/skills/claim-drafting-patterns/SKILL.md`, `.agents/skills/prior-art-search-strategy/SKILL.md`

## Workflow

- Start full-pipeline work with `patent-drafter`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A patent application drafting agent team harness.
