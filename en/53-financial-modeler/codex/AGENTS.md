# Financial Modeler Harness

This folder is the Codex version of the Financial Modeler Harness. Start with the local `financial-modeler` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/financial-modeler/SKILL.md`
- Specialist agents: `.codex/agents/cost-analyst.toml`, `.codex/agents/model-reviewer.toml`, `.codex/agents/revenue-modeler.toml`, `.codex/agents/scenario-planner.toml`, `.codex/agents/valuation-expert.toml`
- Extension skills: `.agents/skills/dcf-valuation/SKILL.md`, `.agents/skills/sensitivity-analysis/SKILL.md`, `.agents/skills/unit-economics/SKILL.md`

## Workflow

- Start full-pipeline work with `financial-modeler`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce the full financial modeling lifecycle: revenue model, cost structure, scenario analysis, and valuation.

## Deliverables

- `00_input.md` — Organized user input
- `01_revenue_model.md` — Revenue model
- `02_cost_structure.md` — Cost structure
- `03_scenario_analysis.md` — Scenario analysis results
- `04_valuation.md` — Valuation report
- `05_review_report.md` — Review report
