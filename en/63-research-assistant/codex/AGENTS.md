# Research Assistant Harness

This folder is the Codex version of the Research Assistant Harness. Start with the local `research-assistant` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/research-assistant/SKILL.md`
- Specialist agents: `.codex/agents/critic-synthesizer.toml`, `.codex/agents/literature-searcher.toml`, `.codex/agents/note-taker.toml`, `.codex/agents/reference-manager.toml`, `.codex/agents/research-coordinator.toml`
- Extension skills: `.agents/skills/citation-formatter/SKILL.md`, `.agents/skills/systematic-review-protocol/SKILL.md`

## Workflow

- Start full-pipeline work with `research-assistant`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for academic research assistance.
