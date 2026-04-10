---
name: exam-prep
description: >-
  Trigger when: the user wants the `exam-prep` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Exam Prep Harness

An agent team harness for exam preparation: exam trend analysis, weakness diagnosis, customized study plans, mock exams, and error analysis.

## Specialist Agents

- `diagnostician`: Diagnostic assessment expert. Measures the learner's current proficiency level by subject area, identifies weaknesses, and provides the foundation for a customized study strategy.
- `error-analyst`: Error analysis expert. Analyzes mock exam results to identify error patterns, diagnose concept deficits, and formulate targeted remediation strategies.
- `examiner`: Mock exam creator. Designs mock exams that match the real exam in format, difficulty, and timing, and writes detailed answer explanations.
- `learning-designer`: Customized study plan designer. Creates a personalized learning curriculum, schedule, and materials based on diagnostic results.
- `trend-analyst`: Exam trend analysis expert. Analyzes past exam question patterns, identifies frequently tested areas, tracks difficulty trends, and predicts likely topics for upcoming exams.

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
- `01_trend_analysis.md` — Exam trend analysis
- `02_diagnosis.md` — Diagnostic results
- `03_study_plan.md` — Study plan
- `04_mock_exam.md` — Mock exam
- `05_error_analysis.md` — Error analysis report
- `06_review_report.md` — Review report

## Extension Skills

- `.agents/skills/bloom-taxonomy-engine/SKILL.md`
- `.agents/skills/error-pattern-analyzer/SKILL.md`
