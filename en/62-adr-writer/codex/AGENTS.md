# ADR Writer Harness

This folder is the Codex version of the ADR Writer Harness. Start with the local `adr-writer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/adr-writer/SKILL.md`
- Specialist agents: `.codex/agents/adr-author.toml`, `.codex/agents/alternative-researcher.toml`, `.codex/agents/context-analyst.toml`, `.codex/agents/impact-tracker.toml`, `.codex/agents/tradeoff-evaluator.toml`
- Extension skills: `.agents/skills/madr-template-engine/SKILL.md`, `.agents/skills/quality-attribute-analyzer/SKILL.md`

## Workflow

- Start full-pipeline work with `adr-writer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for creating Architecture Decision Records (ADRs).
