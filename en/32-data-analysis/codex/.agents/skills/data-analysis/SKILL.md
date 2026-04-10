---
name: data-analysis
description: >-
  Trigger when: the user wants the `data-analysis` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Data Analysis Harness

A harness where an agent team collaborates to perform the full data analysis lifecycle: exploration → cleaning → analysis → visualization → reporting.

## Specialist Agents

- `analyst`: Statistical analysis specialist. Applies appropriate statistical techniques for hypothesis testing, correlation analysis, regression analysis, clustering, and time-series analysis, and interprets results for business decision-making.
- `cleaner`: Data cleaning specialist. Performs missing value treatment, outlier handling, type conversion, duplicate removal, and normalization/standardization, recording all transformations as reproducible code.
- `explorer`: Exploratory Data Analysis (EDA) specialist. Performs data profiling, distribution analysis, missing value pattern analysis, outlier detection, and variable relationship exploration.
- `reporter`: Analysis report writing specialist. Synthesizes EDA, cleaning, analysis, and visualization results to produce a final report for executives/stakeholders, delivering insights and recommendations in a way accessible to non-specialists.
- `visualizer`: Data visualization specialist. Designs charts that effectively communicate analysis results and generates code using matplotlib/seaborn/plotly.

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

- `.agents/skills/statistical-tests-selector/SKILL.md`
- `.agents/skills/visualization-chooser/SKILL.md`
