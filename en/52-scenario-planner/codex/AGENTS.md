# Scenario Planner Harness

This folder is the Codex version of the Scenario Planner Harness. Start with the local `scenario-planner` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/scenario-planner/SKILL.md`
- Specialist agents: `.codex/agents/impact-assessor.toml`, `.codex/agents/integration-reviewer.toml`, `.codex/agents/scenario-designer.toml`, `.codex/agents/strategy-architect.toml`, `.codex/agents/variable-analyst.toml`
- Extension skills: `.agents/skills/decision-trigger-mapper/SKILL.md`, `.agents/skills/scenario-narrative-engine/SKILL.md`, `.agents/skills/steep-framework/SKILL.md`

## Workflow

- Start full-pipeline work with `scenario-planner`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness that defines key variables in uncertain environments, constructs a scenario matrix, and develops impact analysis and response strategies.

## Deliverables

- `00_input.md` — Organized user input
- `01_variable_analysis.md` — Key variable analysis report
- `02_scenario_matrix.md` — Scenario matrix and narratives
- `03_impact_assessment.md` — Impact analysis report
- `04_response_strategy.md` — Response strategy document
- `05_decision_document.md` — Integrated decision document
- `06_review_report.md` — Review report
