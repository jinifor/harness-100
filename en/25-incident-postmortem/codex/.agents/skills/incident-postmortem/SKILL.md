---
name: incident-postmortem
description: >-
  Trigger when: the user wants the `incident-postmortem` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Incident Postmortem Harness

An agent team harness that collaborates to generate incident postmortem reports. Automates the pipeline of timeline reconstruction -> root cause analysis -> impact assessment -> remediation planning -> report generation.

## Specialist Agents

- `impact-assessor`: Impact assessment expert. Quantitatively assesses user impact, revenue impact, SLA impact, and reputation impact of incidents, providing a comprehensive business impact evaluation.
- `postmortem-reviewer`: Postmortem reviewer (QA). Cross-validates consistency across timeline, root cause, impact, and remediation, and ensures blameless culture is maintained.
- `remediation-planner`: Remediation planning expert. Establishes short/mid/long-term countermeasures for root causes and contributing factors, generating actionable action items with ownership and deadlines.
- `root-cause-investigator`: Root cause investigation expert. Traces from surface symptoms to root causes using 5 Whys, Fishbone diagrams, and Fault Tree Analysis.
- `timeline-reconstructor`: Incident timeline reconstruction expert. Collects incident-related events, orders them chronologically, and identifies gaps to reconstruct an accurate incident progression.

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
- `01_timeline.md` — Incident timeline
- `02_root_cause.md` — Root cause analysis
- `03_impact_assessment.md` — Impact assessment
- `04_remediation_plan.md` — Remediation plan
- `05_review_report.md` — Review report
- `postmortem_report.md` — Final integrated postmortem report

## Extension Skills

- `.agents/skills/rca-methodology/SKILL.md`
- `.agents/skills/sla-impact-calculator/SKILL.md`
