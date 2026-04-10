# Compliance Checker Harness

This folder is the Codex version of the Compliance Checker Harness. Start with the local `compliance-checker` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/compliance-checker/SKILL.md`
- Specialist agents: `.codex/agents/gap-analyst.toml`, `.codex/agents/law-mapper.toml`, `.codex/agents/remediation-planner.toml`, `.codex/agents/status-auditor.toml`
- Extension skills: `.agents/skills/audit-checklist-engine/SKILL.md`, `.agents/skills/regulation-knowledge-base/SKILL.md`

## Workflow

- Start full-pipeline work with `compliance-checker`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Regulatory compliance verification — an agent team collaborates to perform law mapping, status audit, gap analysis, and remediation planning.

## Deliverables

- `00_input.md` — Organized user input
- `01_law_mapping.md` — Law mapping report
- `02_status_audit.md` — Status audit report
- `03_gap_analysis.md` — Gap analysis report
- `04_remediation_plan.md` — Remediation plan
