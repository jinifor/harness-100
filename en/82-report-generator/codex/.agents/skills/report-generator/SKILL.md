---
name: report-generator
description: >-
  Trigger when: the user wants the `report-generator` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Report Generator Harness

work report datacollection→analysis→visualization→→summary A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `analyst`: work report analysis. collectiondone datafrom statisticsquality analysis, trend identify, comparison analysis, insight derive performto report core supporting argument composition.
- `data-collector`: work report data collection. report neededKorean ·nature data web search, file analysis, user provide materialfrom systematicas collectionand refinement.
- `executive-summarizer`: work report summary and cross-verification expert(QA). management 1degree summary writingand, data-analysis-visualization-body text between consistency cross-verification.
- `report-writer`: work report writingspecialist. analysis result and visualization integrationto quality persuasioncapability report . reporting target(management/actualspecialist/external) tone and structure applied.
- `visualizer`: work report visualization expert. analysis result chart, , diagramas exchange peopletax writingand, Mermaid/ASCII chart visualization implementation.

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

## Extension Skills

- `.agents/skills/data-visualization-guide/SKILL.md`
- `.agents/skills/kpi-dashboard-patterns/SKILL.md`
