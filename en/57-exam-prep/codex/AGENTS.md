# Exam Prep Harness

This folder is the Codex version of the Exam Prep Harness. Start with the local `exam-prep` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/exam-prep/SKILL.md`
- Specialist agents: `.codex/agents/diagnostician.toml`, `.codex/agents/error-analyst.toml`, `.codex/agents/examiner.toml`, `.codex/agents/learning-designer.toml`, `.codex/agents/trend-analyst.toml`
- Extension skills: `.agents/skills/bloom-taxonomy-engine/SKILL.md`, `.agents/skills/error-pattern-analyzer/SKILL.md`

## Workflow

- Start full-pipeline work with `exam-prep`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for exam preparation: exam trend analysis, weakness diagnosis, customized study plans, mock exams, and error analysis.

## Deliverables

- `00_input.md` — Organized user input
- `01_trend_analysis.md` — Exam trend analysis
- `02_diagnosis.md` — Diagnostic results
- `03_study_plan.md` — Study plan
- `04_mock_exam.md` — Mock exam
- `05_error_analysis.md` — Error analysis report
- `06_review_report.md` — Review report
