# Coding Bootcamp Harness

This folder is the Codex version of the Coding Bootcamp Harness. Start with the local `coding-bootcamp` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/coding-bootcamp/SKILL.md`
- Specialist agents: `.codex/agents/code-reviewer.toml`, `.codex/agents/curriculum-designer.toml`, `.codex/agents/exercise-creator.toml`, `.codex/agents/mentor.toml`
- Extension skills: `.agents/skills/code-kata-generator/SKILL.md`, `.agents/skills/tech-interview-prep/SKILL.md`

## Workflow

- Start full-pipeline work with `coding-bootcamp`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to deliver coding education: curriculum design, hands-on exercises, code review, projects, and portfolio building.

## Deliverables

- `00_input.md` — Organized user input
- `01_curriculum.md` — Curriculum
- `02_exercises.md` — Practice exercises
- `03_code_review.md` — Code review results
- `04_project_guide.md` — Project guide
- `05_review_report.md` — Review report
