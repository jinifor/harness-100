---
name: wedding-planner
description: >-
  Trigger when: the user wants the `wedding-planner` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Wedding Planner Harness

wedding preparation comprehensive timelinedesign→budgetmanagementtable→vendorcomparisontable→checklist→invitationdocument A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `budget-controller`: budget managementspecialist. wedding preparation overall budget itemby allocationand, expense tracking template and cost reduction strategy provide.
- `checklist-builder`: checklist . wedding preparation overall checklist categoryby writingand, invitation document proposal.
- `timeline-designer`: timeline designspecialist. wedding ceremony D-day standardas to monthby·weekby preparation schedule designand, core milestone definition.
- `vendor-analyst`: vendor comparison analysis. wedding hall, studio/dress/makeup, honeymoon etc. key vendor researchand comparisontable writingand optional guide provide.
- `wedding-reviewer`: reviewer(QA). timeline-budget-vendor-checklist between consistency cross-verificationand, ··realistic item findingsto feedback.

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

- `.agents/skills/vendor-negotiation-guide/SKILL.md`
- `.agents/skills/wedding-budget-optimizer/SKILL.md`
