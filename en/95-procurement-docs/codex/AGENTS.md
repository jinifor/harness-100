# Procurement Docs Harness

This folder is the Codex version of the Procurement Docs Harness. Start with the local `procurement-docs` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/procurement-docs/SKILL.md`
- Specialist agents: `.codex/agents/acceptance-builder.toml`, `.codex/agents/contract-reviewer.toml`, `.codex/agents/evaluation-designer.toml`, `.codex/agents/requirements-definer.toml`, `.codex/agents/vendor-comparator.toml`
- Extension skills: `.agents/skills/contract-checklist/SKILL.md`, `.agents/skills/vendor-scoring/SKILL.md`

## Workflow

- Start full-pipeline work with `procurement-docs`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A procurement document set generation harness. An agent team collaborates to produce everything from requirements definition through vendor comparison, evaluation criteria, contract review, and acceptance criteria.
