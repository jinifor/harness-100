# Legacy Modernizer Harness

This folder is the Codex version of the Legacy Modernizer Harness. Start with the local `legacy-modernizer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/legacy-modernizer/SKILL.md`
- Specialist agents: `.codex/agents/legacy-analyzer.toml`, `.codex/agents/migration-engineer.toml`, `.codex/agents/modernization-reviewer.toml`, `.codex/agents/refactoring-strategist.toml`, `.codex/agents/regression-tester.toml`
- Extension skills: `.agents/skills/dependency-analysis/SKILL.md`, `.agents/skills/strangler-fig-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `legacy-modernizer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for transforming legacy codebases into modern architectures. Automates the analysis -> refactoring strategy -> migration -> verification pipeline.

## Deliverables

- `00_input.md` — Organized user input
- `01_legacy_analysis.md` — Legacy analysis report
- `02_refactoring_strategy.md` — Refactoring strategy document
- `03_migration_plan.md` — Migration execution plan and code
- `04_test_report.md` — Regression test report
- `05_review_report.md` — Final review report
