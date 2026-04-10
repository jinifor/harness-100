---
name: compliance-checker
description: >-
  Trigger when: the user wants the `compliance-checker` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Compliance Checker Harness

Regulatory compliance verification — an agent team collaborates to perform law mapping, status audit, gap analysis, and remediation planning.

## Specialist Agents

- `gap-analyst`: Gap analyst. Analyzes the differences between legal requirements and current compliance status, calculates risk, and derives corrective action priorities.
- `law-mapper`: Compliance law analyst. Identifies laws, regulations, and standards applicable to the target business/service, and structures and maps obligations by clause.
- `remediation-planner`: Remediation planner. Based on gap analysis results, designs specific corrective action plans, schedules, responsibility assignments, and monitoring frameworks.
- `status-auditor`: Status auditor. Investigates the organization's current regulatory compliance state, collects and classifies evidence, and assesses compliance status for each obligation.

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
- `01_law_mapping.md` — Law mapping report
- `02_status_audit.md` — Status audit report
- `03_gap_analysis.md` — Gap analysis report
- `04_remediation_plan.md` — Remediation plan

## Extension Skills

- `.agents/skills/audit-checklist-engine/SKILL.md`
- `.agents/skills/regulation-knowledge-base/SKILL.md`
