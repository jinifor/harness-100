# Market Research Harness

This folder is the Codex version of the Market Research Harness. Start with the local `market-research` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/market-research/SKILL.md`
- Specialist agents: `.codex/agents/competitor-analyst.toml`, `.codex/agents/consumer-analyst.toml`, `.codex/agents/industry-analyst.toml`, `.codex/agents/research-reviewer.toml`, `.codex/agents/trend-analyst.toml`
- Extension skills: `.agents/skills/porter-five-forces/SKILL.md`, `.agents/skills/tam-sam-som-calculator/SKILL.md`

## Workflow

- Start full-pipeline work with `market-research`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Market research: a harness where an agent team collaborates to perform industry analysis → competitor analysis → consumer analysis → trend analysis → research review.
