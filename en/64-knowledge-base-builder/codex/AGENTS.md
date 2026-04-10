# Knowledge Base Builder Harness

This folder is the Codex version of the Knowledge Base Builder Harness. Start with the local `knowledge-base-builder` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/knowledge-base-builder/SKILL.md`
- Specialist agents: `.codex/agents/knowledge-collector.toml`, `.codex/agents/maintenance-planner.toml`, `.codex/agents/search-optimizer.toml`, `.codex/agents/taxonomy-designer.toml`, `.codex/agents/wiki-builder.toml`
- Extension skills: `.agents/skills/content-lifecycle-manager/SKILL.md`, `.agents/skills/information-architecture/SKILL.md`

## Workflow

- Start full-pipeline work with `knowledge-base-builder`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for building organizational knowledge management systems.
