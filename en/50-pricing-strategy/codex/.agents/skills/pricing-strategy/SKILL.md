---
name: pricing-strategy
description: >-
  Trigger when: the user wants the `pricing-strategy` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Pricing Strategy Harness

Develop a pricing strategy: an agent team collaborates to produce cost analysis, competitive pricing, value-based pricing, and simulations.

## Specialist Agents

- `competitive-analyst`: Competitive pricing analysis expert. Investigates competitor pricing structures in the market and analyzes price positioning maps, feature-price comparisons, and pricing strategy patterns.
- `cost-analyst`: Cost analysis expert. Analyzes direct and indirect costs of products/services, and calculates break-even point (BEP), margin structure, and cost-based price floor.
- `pricing-reviewer`: Pricing strategy reviewer (QA). Cross-validates consistency across cost, competitive, value, and simulation analyses, and evaluates the logical coherence and feasibility of the pricing strategy.
- `pricing-simulator`: Pricing simulation expert. Designs various pricing scenarios and performs demand elasticity, P&L impact, and sensitivity analysis to derive optimal pricing strategy.
- `value-assessor`: Value-based pricing expert. Analyzes perceived customer value (WTP, Willingness to Pay), value drivers, and derives optimal pricing by customer segment.

## Workflow

1. Gather the request, constraints, and any existing source material.
2. Save the starting context in `_workspace/00_input.md` when that helps downstream handoff.
3. Run the specialists needed for the request scope, using numbered `_workspace/` artifacts as handoff points.
4. Run the reviewer or synthesizer role, if present, after prerequisite artifacts exist.
5. Report skipped phases, limitations, and reused inputs in the final result.

## Output Rules

- Keep the source `.claude` files untouched.
- Keep all harness deliverables in `_workspace/`.
- If existing files already satisfy a phase, reference or copy them into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Deliverables

- `00_input.md` — Organized user input
- `01_cost_analysis.md` — Cost analysis report
- `02_competitive_pricing.md` — Competitive pricing analysis report
- `03_value_pricing.md` — Value-based pricing analysis report
- `04_pricing_simulation.md` — Pricing simulation report
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/price-elasticity-calculator/SKILL.md`
- `.agents/skills/psm-analyzer/SKILL.md`
