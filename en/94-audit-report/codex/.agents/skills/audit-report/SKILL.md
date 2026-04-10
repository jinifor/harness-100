---
name: audit-report
description: >-
  Trigger when: the user wants the `audit-report` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Audit Report Harness

An internal audit report generation harness. An agent team collaborates to handle everything from audit scope design through checklist creation, findings analysis, improvement recommendations, and tracking ledger management.

## Specialist Agents

- `checklist-builder`: Audit checklist creation expert. Breaks down audit criteria into specific control items, test procedures, and evidence requirements to create field-ready checklists.
- `findings-analyst`: Audit findings analysis expert. Structures findings based on checklist results, assigns risk ratings, and performs root cause analysis and impact assessment.
- `recommendation-writer`: Improvement recommendation writing expert. Designs corrective actions for each finding and produces actionable improvement recommendations including implementation plans, expected benefits, and priorities.
- `scope-designer`: Audit scope design expert. Defines audit objectives, applicable standards (laws/regulations/policies), audit targets, audit period, and resource allocation, and produces the audit plan.
- `tracking-manager`: Implementation tracking ledger management expert. Tracks corrective action implementation status for audit findings and manages follow-up actions, closure criteria, and escalation procedures.

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

- `.agents/skills/finding-classification/SKILL.md`
- `.agents/skills/internal-control-framework/SKILL.md`
