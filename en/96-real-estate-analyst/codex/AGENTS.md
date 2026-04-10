# Real Estate Analyst Harness

This folder is the Codex version of the Real Estate Analyst Harness. Start with the local `real-estate-analyst` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/real-estate-analyst/SKILL.md`
- Specialist agents: `.codex/agents/location-analyst.toml`, `.codex/agents/market-researcher.toml`, `.codex/agents/profitability-analyst.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/risk-assessor.toml`
- Extension skills: `.agents/skills/cap-rate-calculator/SKILL.md`, `.agents/skills/location-scoring/SKILL.md`

## Workflow

- Start full-pipeline work with `real-estate-analyst`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A real estate analysis harness. An agent team collaborates to produce market research, location analysis, profitability analysis, risk assessment, and investment reports.
