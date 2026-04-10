---
name: risk-register
description: >-
  Trigger when: the user wants the `risk-register` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Risk Register Harness

project risk managementversus: riskidentification→probability·impactassessment→responsestrategyestablish→monitoringplan→statusreportto A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `assessment-analyst`: risk assessment analysis. probability·impact matrix, expectedtransfervalue(EMV), risk score , priority decision perform.
- `monitoring-planner`: risk monitoring designspecialist. KRI(coreriskindicator), condition, monitoring cycle, review process design.
- `report-writer`: risk status report writingspecialist. management dashboard, trend analysis, risk includedKorean comprehensive risk report writing.
- `response-strategist`: risk response strategy. riskby quality response strategy(avoidance/transfer/mitigation/acceptance) establishand, response plan and residual risk management.
- `risk-identifier`: risk identification expert. project nature systematic risk identification, RBS(Risk Breakdown Structure) writing, risk categoryby derive perform.

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

- `.agents/skills/risk-response-patterns/SKILL.md`
- `.agents/skills/risk-scoring-matrix/SKILL.md`
