---
name: course-builder
description: >-
  Trigger when: the user wants the `course-builder` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Course Builder Harness

A harness where an agent team collaborates to produce online courses from curriculum design through lesson plans, quizzes, and hands-on labs.

## Specialist Agents

- `content-writer`: Course content writer. Creates per-lesson lesson plans, presentation slide outlines, instructor notes, and learner handouts based on the curriculum.
- `course-reviewer`: Course reviewer (QA). Cross-validates learning objective alignment across curriculum, lesson plans, quizzes, and labs. Identifies difficulty inconsistencies, coverage gaps, and quality issues.
- `curriculum-designer`: Curriculum designer. Establishes learning objectives, designs curriculum structure, breaks content into modules and lessons, maps prerequisites, and designs learning paths. Follows the ADDIE model and Bloom's Taxonomy for systematic instructional design.
- `lab-designer`: Lab designer. Designs hands-on labs, mini projects, and capstone projects aligned to learning objectives. Includes rubrics, sample solutions, and scaffolding.
- `quiz-maker`: Quiz maker. Designs formative assessments (per-lesson quizzes) and summative assessments (module/course exams) aligned to learning objectives. Includes diverse item types and feedback based on Bloom's Taxonomy.

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
- `01_curriculum.md` — Curriculum / course design document
- `02_lesson_plans.md` — Lesson plans / instructor notes
- `03_quizzes.md` — Quizzes / assessment items
- `04_labs.md` — Hands-on labs / projects
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/assessment-engineering/SKILL.md`
- `.agents/skills/lab-scaffolding/SKILL.md`
- `.agents/skills/learning-design/SKILL.md`
