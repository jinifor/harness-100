---
name: onboarding-system
description: >-
  Trigger when: the user wants the `onboarding-system` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Onboarding System Harness

New hire onboarding: A harness where an agent team collaborates to generate everything from checklists to training, mentor assignments, and 30-60-90 day plans.

## Specialist Agents

- `experience-reviewer`: Onboarding experience reviewer. Cross-validates the overall program for consistency, identifies improvements, and produces the final report.
- `mentor-matcher`: Mentor/buddy matching expert. Defines mentor/buddy roles, establishes matching criteria, creates mentor guides, and designs relationship management processes.
- `milestone-tracker`: 30-60-90 day milestone designer. Designs stage-by-stage goals, performance criteria, feedback systems, and progress tracking.
- `onboarding-architect`: Onboarding architect. Designs the onboarding checklist, schedule, milestones, and stakeholder roles from pre-boarding through the first 90 days.
- `training-builder`: Training content builder. Designs onboarding training curriculum, learning materials, quizzes, and self-assessments.

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

- `.agents/skills/buddy-program-guide/SKILL.md`
- `.agents/skills/learning-path-design/SKILL.md`
