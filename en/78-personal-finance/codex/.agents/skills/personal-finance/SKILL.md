---
name: personal-finance
description: >-
  Trigger when: the user wants the `personal-finance` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Personal Finance Harness

itemsperson financialmanagement incomeexpenseanalysis→budgetdesign→investmentstrategy→tax savingsapproach→retirementdesign A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `budget-planner`: budget designspecialist. financial analysis result as categoryby month budget designand, savings goal and actual strategy establish.
- `finance-reviewer`: financial reviewer(QA). analysis-budget-investment-tax savings between consistency cross-verificationand, figure accuracy, execution possiblenature, risk person comprehensive assessment.
- `financial-analyst`: financial analysis. user income·expense structure analysisand, financial casebeforenature diagnosisand, improvement point derive.
- `investment-advisor`: investment expert. user investment nature, goal, duration assetallocation strategy and portfolio design.
- `tax-strategist`: tax strategy. structure tax savings approach establishand, tax maximization strategy and retirement design provide.

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

## Extension Skills

- `.agents/skills/compound-interest-simulator/SKILL.md`
- `.agents/skills/financial-ratio-analyzer/SKILL.md`
