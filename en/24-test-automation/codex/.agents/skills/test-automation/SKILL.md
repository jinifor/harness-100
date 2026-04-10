---
name: test-automation
description: >-
  Trigger when: the user wants the `test-automation` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Test Automation Harness

An agent team harness that collaborates on test automation strategy development, test writing, CI integration, and coverage analysis.

## Specialist Agents

- `coverage-analyst`: Coverage analysis expert. Measures test coverage, identifies coverage gaps, and determines additional test priorities based on risk.
- `integration-tester`: Integration testing expert. Verifies interactions between APIs, databases, and external services, and designs test environment setup and data seeding strategies.
- `qa-reviewer`: Test automation reviewer (QA). Cross-validates consistency between strategy, tests, and coverage, and evaluates test quality and maintainability.
- `test-strategist`: Test strategy expert. Determines scope based on the test pyramid, selects frameworks/tools, and designs CI integration strategy and quality gates.
- `unit-tester`: Unit testing expert. Writes unit tests for business logic, designs mocking strategies, and derives effective test cases using boundary value analysis and equivalence partitioning.

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
- `01_test_strategy.md` — Test strategy document
- `02_unit_tests.md` — Unit test code and guide
- `03_integration_tests.md` — Integration test code and guide
- `04_coverage_report.md` — Coverage analysis report
- `05_review_report.md` — Final review report

## Extension Skills

- `.agents/skills/mocking-strategy/SKILL.md`
- `.agents/skills/test-design-patterns/SKILL.md`
