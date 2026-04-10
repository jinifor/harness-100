# Test Automation Harness

This folder is the Codex version of the Test Automation Harness. Start with the local `test-automation` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/test-automation/SKILL.md`
- Specialist agents: `.codex/agents/coverage-analyst.toml`, `.codex/agents/integration-tester.toml`, `.codex/agents/qa-reviewer.toml`, `.codex/agents/test-strategist.toml`, `.codex/agents/unit-tester.toml`
- Extension skills: `.agents/skills/mocking-strategy/SKILL.md`, `.agents/skills/test-design-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `test-automation`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness that collaborates on test automation strategy development, test writing, CI integration, and coverage analysis.

## Deliverables

- `00_input.md` — Organized user input
- `01_test_strategy.md` — Test strategy document
- `02_unit_tests.md` — Unit test code and guide
- `03_integration_tests.md` — Integration test code and guide
- `04_coverage_report.md` — Coverage analysis report
- `05_review_report.md` — Final review report
