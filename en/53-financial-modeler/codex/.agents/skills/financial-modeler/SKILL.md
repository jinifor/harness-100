---
name: financial-modeler
description: >-
  Trigger when: the user wants the `financial-modeler` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Financial Modeler Harness

A harness where an agent team collaborates to produce the full financial modeling lifecycle: revenue model, cost structure, scenario analysis, and valuation.

## Specialist Agents

- `cost-analyst`: Cost structure analysis expert. Classifies fixed and variable costs, designs cost structures to calculate break-even points, and derives cost optimization strategies.
- `model-reviewer`: Financial model reviewer (QA). Cross-validates formula accuracy, assumption consistency, and logical validity across revenue model, cost structure, scenarios, and valuation.
- `revenue-modeler`: Revenue model design expert. Defines business revenue streams and builds revenue forecast models through pricing strategy, sales volume estimation, and growth rate scenarios.
- `scenario-planner`: Financial scenario analysis expert. Constructs Base/Bull/Bear scenarios and performs sensitivity analysis on key variables to calculate the range of financial performance variation.
- `valuation-expert`: Valuation expert. Applies various valuation methodologies including DCF, multiples, and comparable company analysis to calculate enterprise value and provide the basis for investment decisions.

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
- `01_revenue_model.md` — Revenue model
- `02_cost_structure.md` — Cost structure
- `03_scenario_analysis.md` — Scenario analysis results
- `04_valuation.md` — Valuation report
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/dcf-valuation/SKILL.md`
- `.agents/skills/sensitivity-analysis/SKILL.md`
- `.agents/skills/unit-economics/SKILL.md`
