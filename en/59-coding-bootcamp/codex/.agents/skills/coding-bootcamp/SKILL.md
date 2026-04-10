---
name: coding-bootcamp
description: >-
  Trigger when: the user wants the `coding-bootcamp` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Coding Bootcamp Harness

A harness where an agent team collaborates to deliver coding education: curriculum design, hands-on exercises, code review, projects, and portfolio building.

## Specialist Agents

- `code-reviewer`: Code reviewer. Reviews learner code from quality, readability, performance, and pattern perspectives, providing specific improvement guidance.
- `curriculum-designer`: Curriculum designer. Creates step-by-step learning paths, selects tech stacks, and designs weekly schedules tailored to the learner's level and goals.
- `exercise-creator`: Exercise creator. Designs coding problems by difficulty level, with test cases and solution guides, aligned to the curriculum.
- `mentor`: Developer mentor. Provides real-world project design, portfolio building, technical interview preparation, and career guidance.

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
- `01_curriculum.md` — Curriculum
- `02_exercises.md` — Practice exercises
- `03_code_review.md` — Code review results
- `04_project_guide.md` — Project guide
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/code-kata-generator/SKILL.md`
- `.agents/skills/tech-interview-prep/SKILL.md`
