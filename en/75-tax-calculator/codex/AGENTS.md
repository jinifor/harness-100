# Tax Calculator Harness

This folder is the Codex version of the Tax Calculator Harness. Start with the local `tax-calculator` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/tax-calculator/SKILL.md`
- Specialist agents: `.codex/agents/deduction-optimizer.toml`, `.codex/agents/income-analyst.toml`, `.codex/agents/strategy-advisor.toml`, `.codex/agents/tax-engine.toml`
- Extension skills: `.agents/skills/deduction-optimizer-engine/SKILL.md`, `.agents/skills/tax-bracket-simulator/SKILL.md`

## Workflow

- Start full-pipeline work with `tax-calculator`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A tax calculation agent team harness.
