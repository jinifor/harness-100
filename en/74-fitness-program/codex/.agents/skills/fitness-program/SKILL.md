---
name: fitness-program
description: >-
  Trigger when: the user wants the `fitness-program` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Fitness Program Harness

A fitness program design agent team harness.

## Specialist Agents

- `exercise-guide`: exercise-guide specialist.
- `nutrition-linker`: Nutrition integration specialist. Develops nutrition strategies aligned with exercise programs and provides pre/post-workout nutrition timing, supplement, and hydration guides.
- `program-architect`: Exercise program designer. Analyzes the user's goals, fitness level, and available time to design periodized training programs, optimizing volume, intensity, and frequency.
- `template-builder`: Template builder. Creates templates for tracking and managing program progress, including workout logs, body composition trackers, progress photo guides, and periodic assessment forms.

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

- `.agents/skills/exercise-biomechanics/SKILL.md`
- `.agents/skills/periodization-engine/SKILL.md`
