---
name: ml-experiment
description: >-
  Trigger when: the user wants the `ml-experiment` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# ML Experiment Harness

A harness where an agent team collaborates to perform the full ML experiment lifecycle: data preparation → model design → training → evaluation → deployment.

## Specialist Agents

- `data-engineer`: ML Data Engineer. Performs data collection, exploratory analysis (EDA), preprocessing, feature engineering, data splitting, and data version management to build optimized datasets for training.
- `evaluation-analyst`: Evaluation Analyst. Analyzes model performance metrics, performs error analysis, bias verification, interpretability (XAI), deployment readiness assessment, and A/B test design.
- `experiment-reviewer`: Experiment Reviewer (QA). Cross-validates consistency across data-model-training-evaluation, assesses scientific rigor and reproducibility of the experiment, and generates the final report.
- `model-designer`: Model Designer. Designs ML/DL model architectures, defines hyperparameter spaces, selects loss functions, establishes regularization strategies, and implements model code.
- `training-manager`: Training Manager. Handles experiment tracking (MLflow/W&B), GPU resource management, training loop implementation, checkpoint management, reproducibility assurance, and hyperparameter tuning.

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

- `.agents/skills/experiment-tracking-setup/SKILL.md`
- `.agents/skills/feature-engineering-cookbook/SKILL.md`
- `.agents/skills/model-selection-guide/SKILL.md`
