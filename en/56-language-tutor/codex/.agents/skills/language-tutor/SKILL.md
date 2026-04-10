---
name: language-tutor
description: >-
  Trigger when: the user wants the `language-tutor` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Language Tutor Harness

An agent team harness for foreign language learning: level testing, curriculum design, lessons, quizzes, and review management.

## Specialist Agents

- `curriculum-designer`: Foreign language curriculum design expert. Designs customized curricula including learning objectives, phased study plans, textbook selection, and milestones based on level assessment results.
- `lesson-tutor`: Foreign language lesson tutor. Generates specific lesson materials including grammar explanations, vocabulary learning, conversation practice, and reading/writing tasks according to the curriculum.
- `level-assessor`: Foreign language level assessment expert. Designs and administers CEFR-based diagnostic tests to precisely evaluate the learner's current level and analyze strengths and weaknesses by skill area.
- `quiz-master`: Foreign language quiz expert. Creates various types of quizzes based on learned content, adjusts difficulty levels, and provides accurate scoring criteria and feedback.
- `review-coach`: Review coach. Designs spaced repetition learning based on the Ebbinghaus forgetting curve, develops weakness reinforcement plans, and manages overall learning progress.

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
- `01_level_assessment.md` — Level test results
- `02_curriculum.md` — Learning curriculum
- `03_lessons.md` — Lesson materials
- `04_quizzes.md` — Quizzes
- `05_review_plan.md` — Review plan
- `06_review_report.md` — Review report

## Extension Skills

- `.agents/skills/cefr-assessment/SKILL.md`
- `.agents/skills/spaced-repetition/SKILL.md`
