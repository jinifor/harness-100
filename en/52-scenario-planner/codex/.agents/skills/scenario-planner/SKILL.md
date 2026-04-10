---
name: scenario-planner
description: >-
  Trigger when: the user wants the `scenario-planner` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Scenario Planner Harness

An agent team harness that defines key variables in uncertain environments, constructs a scenario matrix, and develops impact analysis and response strategies.

## Specialist Agents

- `impact-assessor`: Per-scenario impact assessment expert. Analyzes the quantitative and qualitative impact of each scenario on the organization's strategy, finances, operations, and workforce, and systematically evaluates risks and opportunities.
- `integration-reviewer`: Scenario planning integration reviewer (QA). Cross-validates logical consistency across variable analysis, scenario matrix, impact analysis, and response strategy, and edits the final integrated decision document.
- `scenario-designer`: Scenario matrix designer. Constructs 2x2 or 3x3 scenario matrices based on key variable axes and writes the narrative and development path for each scenario.
- `strategy-architect`: Response strategy development expert. Based on per-scenario impact analysis results, designs robust strategies, hedge strategies, and option strategies, and writes integrated decision documents.
- `variable-analyst`: Key variable analyst for scenario planning. Identifies critical uncertainty variables affecting decision-making, analyzes correlations between variables, and determines scenario axes.

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
- `01_variable_analysis.md` — Key variable analysis report
- `02_scenario_matrix.md` — Scenario matrix and narratives
- `03_impact_assessment.md` — Impact analysis report
- `04_response_strategy.md` — Response strategy document
- `05_decision_document.md` — Integrated decision document
- `06_review_report.md` — Review report

## Extension Skills

- `.agents/skills/decision-trigger-mapper/SKILL.md`
- `.agents/skills/scenario-narrative-engine/SKILL.md`
- `.agents/skills/steep-framework/SKILL.md`
