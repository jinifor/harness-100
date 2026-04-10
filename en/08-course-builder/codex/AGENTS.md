# Course Builder Harness

This folder is the Codex version of the Course Builder Harness. Start with the local `course-builder` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/course-builder/SKILL.md`
- Specialist agents: `.codex/agents/content-writer.toml`, `.codex/agents/course-reviewer.toml`, `.codex/agents/curriculum-designer.toml`, `.codex/agents/lab-designer.toml`, `.codex/agents/quiz-maker.toml`
- Extension skills: `.agents/skills/assessment-engineering/SKILL.md`, `.agents/skills/lab-scaffolding/SKILL.md`, `.agents/skills/learning-design/SKILL.md`

## Workflow

- Start full-pipeline work with `course-builder`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce online courses from curriculum design through lesson plans, quizzes, and hands-on labs.

## Deliverables

- `00_input.md` — Organized user input
- `01_curriculum.md` — Curriculum / course design document
- `02_lesson_plans.md` — Lesson plans / instructor notes
- `03_quizzes.md` — Quizzes / assessment items
- `04_labs.md` — Hands-on labs / projects
- `05_review_report.md` — Review report
