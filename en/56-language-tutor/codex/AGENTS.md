# Language Tutor Harness

This folder is the Codex version of the Language Tutor Harness. Start with the local `language-tutor` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/language-tutor/SKILL.md`
- Specialist agents: `.codex/agents/curriculum-designer.toml`, `.codex/agents/lesson-tutor.toml`, `.codex/agents/level-assessor.toml`, `.codex/agents/quiz-master.toml`, `.codex/agents/review-coach.toml`
- Extension skills: `.agents/skills/cefr-assessment/SKILL.md`, `.agents/skills/spaced-repetition/SKILL.md`

## Workflow

- Start full-pipeline work with `language-tutor`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for foreign language learning: level testing, curriculum design, lessons, quizzes, and review management.

## Deliverables

- `00_input.md` — Organized user input
- `01_level_assessment.md` — Level test results
- `02_curriculum.md` — Learning curriculum
- `03_lessons.md` — Lesson materials
- `04_quizzes.md` — Quizzes
- `05_review_plan.md` — Review plan
- `06_review_report.md` — Review report
