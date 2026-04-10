---
name: hiring-pipeline
description: >-
  Trigger when: the user wants the `hiring-pipeline` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Hiring Pipeline Harness

hiring process: JDwriting→sourcing→screening→interview→assessment→offerto A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `interview-designer`: interview designspecialist. structure interview, competency based question, interviewer guide, evaluation form design.
- `jd-writer`: JD writing expert. jobanalysis, competencydefinition, job description(Job Description), hiringposting writing.
- `offer-coordinator`: assessment·offer total. final afterreport assessment comprehensive, report package design, offer writing, onboarding annualtotal responsible.
- `screening-expert`: screening expert. from assessment standard, companybefore task design, before/ screening guide writing.
- `sourcing-specialist`: sourcing expert. hiring channel strategy, Full building, value message, hiring responsible.

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

- `.agents/skills/competency-model/SKILL.md`
- `.agents/skills/interview-scorecard/SKILL.md`
