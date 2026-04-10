# Contract Analyzer Harness

This folder is the Codex version of the Contract Analyzer Harness. Start with the local `contract-analyzer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/contract-analyzer/SKILL.md`
- Specialist agents: `.codex/agents/clause-analyst.toml`, `.codex/agents/clause-drafter.toml`, `.codex/agents/comparison-reviewer.toml`, `.codex/agents/contract-coordinator.toml`, `.codex/agents/risk-assessor.toml`
- Extension skills: `.agents/skills/clause-risk-database/SKILL.md`, `.agents/skills/negotiation-playbook/SKILL.md`

## Workflow

- Start full-pipeline work with `contract-analyzer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A contract analysis agent team harness.
