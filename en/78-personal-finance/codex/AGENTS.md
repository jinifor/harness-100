# Personal Finance Harness

This folder is the Codex version of the Personal Finance Harness. Start with the local `personal-finance` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/personal-finance/SKILL.md`
- Specialist agents: `.codex/agents/budget-planner.toml`, `.codex/agents/finance-reviewer.toml`, `.codex/agents/financial-analyst.toml`, `.codex/agents/investment-advisor.toml`, `.codex/agents/tax-strategist.toml`
- Extension skills: `.agents/skills/compound-interest-simulator/SKILL.md`, `.agents/skills/financial-ratio-analyzer/SKILL.md`

## Workflow

- Start full-pipeline work with `personal-finance`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- itemsperson financialmanagement incomeexpenseanalysis→budgetdesign→investmentstrategy→tax savingsapproach→retirementdesign A harness where an agent team collaborates to produce deliverables.
