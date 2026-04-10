---
name: event-organizer
description: >-
  Trigger when: the user wants the `event-organizer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Event Organizer Harness

event basis·operations: concept→venue→program→promotion→execution→companyafterassessmentto A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `concept-planner`: event concept basisspecialist. event goal, , target attendee, budget framework, core nature indicator design.
- `evaluation-analyst`: companyafter assessment analysis. KPI , attendee document, ROI analysis, derive, companyafter report writing.
- `logistics-manager`: logistics . venue , between arrangement, flow of movement design, equipment/technical, catering, planbefore management responsible.
- `program-designer`: program specialist. event , tax composition, speaker management, content design.
- `promotion-lead`: promotion responsible. channelby promotion strategy, content work, etc.record management, attendee communication responsible.

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

- `.agents/skills/budget-planning/SKILL.md`
- `.agents/skills/venue-evaluation/SKILL.md`
