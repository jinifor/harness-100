# Pricing Strategy Harness

This folder is the Codex version of the Pricing Strategy Harness. Start with the local `pricing-strategy` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/pricing-strategy/SKILL.md`
- Specialist agents: `.codex/agents/competitive-analyst.toml`, `.codex/agents/cost-analyst.toml`, `.codex/agents/pricing-reviewer.toml`, `.codex/agents/pricing-simulator.toml`, `.codex/agents/value-assessor.toml`
- Extension skills: `.agents/skills/price-elasticity-calculator/SKILL.md`, `.agents/skills/psm-analyzer/SKILL.md`

## Workflow

- Start full-pipeline work with `pricing-strategy`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Develop a pricing strategy: an agent team collaborates to produce cost analysis, competitive pricing, value-based pricing, and simulations.

## Deliverables

- `00_input.md` — Organized user input
- `01_cost_analysis.md` — Cost analysis report
- `02_competitive_pricing.md` — Competitive pricing analysis report
- `03_value_pricing.md` — Value-based pricing analysis report
- `04_pricing_simulation.md` — Pricing simulation report
- `05_review_report.md` — Review report
