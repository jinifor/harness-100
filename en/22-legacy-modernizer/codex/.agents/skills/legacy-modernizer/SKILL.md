---
name: legacy-modernizer
description: >-
  Trigger when: the user wants the `legacy-modernizer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Legacy Modernizer Harness

An agent team harness for transforming legacy codebases into modern architectures. Automates the analysis -> refactoring strategy -> migration -> verification pipeline.

## Specialist Agents

- `legacy-analyzer`: Legacy code analysis expert. Identifies technical debt in the codebase, maps dependency graphs, measures complexity, and determines modernization priorities.
- `migration-engineer`: Migration execution engineer. Performs actual code transformation, API modernization, framework migration, and configuration externalization according to the refactoring strategy, and generates migration scripts.
- `modernization-reviewer`: Modernization project reviewer (QA). Cross-validates consistency across analysis, strategy, migration, and testing, identifying gaps, contradictions, and risks to provide feedback.
- `refactoring-strategist`: Refactoring strategy expert. Selects optimal refactoring patterns based on legacy analysis results, determines priorities using a risk-impact matrix, and designs a phased migration roadmap.
- `regression-tester`: Regression testing expert. Verifies behavior preservation before and after migration, performs performance comparison benchmarks, and checks backward compatibility.

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
- `01_legacy_analysis.md` — Legacy analysis report
- `02_refactoring_strategy.md` — Refactoring strategy document
- `03_migration_plan.md` — Migration execution plan and code
- `04_test_report.md` — Regression test report
- `05_review_report.md` — Final review report

## Extension Skills

- `.agents/skills/dependency-analysis/SKILL.md`
- `.agents/skills/strangler-fig-patterns/SKILL.md`
