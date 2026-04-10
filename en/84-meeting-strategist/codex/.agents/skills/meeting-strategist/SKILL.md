---
name: meeting-strategist
description: >-
  Trigger when: the user wants the `meeting-strategist` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Meeting Strategist Harness

meeting strategy document agenda itemstructuredesign→backgroundmaterialresearch→decision-makingframework→meetingrecordtemplate→ A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `agenda-architect`: meeting agenda item designspecialist. meeting purpose people definitionand, agenda item structure, time allocation, attendee role, progress method design.
- `background-researcher`: meeting background researchKRW. each agenda item neededKorean data, case, stakeholder analysis, before meeting decisionmatters researchto attendee judgment degreeKRW writing.
- `followup-planner`: meeting and cross-verification expert(QA). meeting after execution plan establishand, agenda item-background-framework-template between consistency cross-verification.
- `framework-designer`: decision-making framework designspecialist. meetingfrom decision-making agenda item regarding judgment standard, option comparison matrix, risk assessment, derive method design.
- `template-builder`: meeting document template . meetingrecord, decisionmatters basisrecorddegree, table , report etc. meeting operations neededKorean all document template creation.

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

- `.agents/skills/decision-frameworks/SKILL.md`
- `.agents/skills/facilitation-techniques/SKILL.md`
