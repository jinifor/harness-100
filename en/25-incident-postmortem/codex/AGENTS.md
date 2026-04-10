# Incident Postmortem Harness

This folder is the Codex version of the Incident Postmortem Harness. Start with the local `incident-postmortem` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/incident-postmortem/SKILL.md`
- Specialist agents: `.codex/agents/impact-assessor.toml`, `.codex/agents/postmortem-reviewer.toml`, `.codex/agents/remediation-planner.toml`, `.codex/agents/root-cause-investigator.toml`, `.codex/agents/timeline-reconstructor.toml`
- Extension skills: `.agents/skills/rca-methodology/SKILL.md`, `.agents/skills/sla-impact-calculator/SKILL.md`

## Workflow

- Start full-pipeline work with `incident-postmortem`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness that collaborates to generate incident postmortem reports. Automates the pipeline of timeline reconstruction -> root cause analysis -> impact assessment -> remediation planning -> report generation.

## Deliverables

- `00_input.md` — Organized user input
- `01_timeline.md` — Incident timeline
- `02_root_cause.md` — Root cause analysis
- `03_impact_assessment.md` — Impact assessment
- `04_remediation_plan.md` — Remediation plan
- `05_review_report.md` — Review report
- `postmortem_report.md` — Final integrated postmortem report
