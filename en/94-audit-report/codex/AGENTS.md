# Audit Report Harness

This folder is the Codex version of the Audit Report Harness. Start with the local `audit-report` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/audit-report/SKILL.md`
- Specialist agents: `.codex/agents/checklist-builder.toml`, `.codex/agents/findings-analyst.toml`, `.codex/agents/recommendation-writer.toml`, `.codex/agents/scope-designer.toml`, `.codex/agents/tracking-manager.toml`
- Extension skills: `.agents/skills/finding-classification/SKILL.md`, `.agents/skills/internal-control-framework/SKILL.md`

## Workflow

- Start full-pipeline work with `audit-report`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An internal audit report generation harness. An agent team collaborates to handle everything from audit scope design through checklist creation, findings analysis, improvement recommendations, and tracking ledger management.
