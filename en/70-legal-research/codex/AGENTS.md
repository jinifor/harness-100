# Legal Research Harness

This folder is the Codex version of the Legal Research Harness. Start with the local `legal-research` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/legal-research/SKILL.md`
- Specialist agents: `.codex/agents/case-searcher.toml`, `.codex/agents/legal-analyst.toml`, `.codex/agents/opinion-writer.toml`, `.codex/agents/strategy-advisor.toml`
- Extension skills: `.agents/skills/case-analysis-framework/SKILL.md`, `.agents/skills/legal-writing-methodology/SKILL.md`

## Workflow

- Start full-pipeline work with `legal-research`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A legal research agent team harness.
