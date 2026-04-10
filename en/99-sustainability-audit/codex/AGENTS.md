# Sustainability Audit Harness

This folder is the Codex version of the Sustainability Audit Harness. Start with the local `sustainability-audit` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/sustainability-audit/SKILL.md`
- Specialist agents: `.codex/agents/environmental-analyst.toml`, `.codex/agents/esg-reporter.toml`, `.codex/agents/governance-reviewer.toml`, `.codex/agents/improvement-planner.toml`, `.codex/agents/social-assessor.toml`
- Extension skills: `.agents/skills/ghg-protocol/SKILL.md`, `.agents/skills/materiality-assessment/SKILL.md`

## Workflow

- Start full-pipeline work with `sustainability-audit`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A sustainability audit harness. An agent team collaborates to produce environmental analysis, social assessment, governance review, ESG reporting, and improvement planning.
