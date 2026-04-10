---
name: proposal-writer
description: >-
  Trigger when: the user wants the `proposal-writer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Proposal Writer Harness

proposal clientanalysis→solutiondesign→price→differentiation→specialistperson A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `client-analyst`: proposal client analysis. re- client current status, task, decision-making structure, competition situation analysisto proposal strategyquality direction establish.
- `differentiator`: proposal differentiation strategy. specialistcompany inherentKorean strength(USP), competitionadvantage, results/reference utilizationto competition proposal versus optional number differentiation strategy establish.
- `pricing-strategist`: proposal price strategy. KRW analysis, price model design, competition price comparison, ROI calculation, to doperson/person strategy establish.
- `proposal-designer`: proposal integration specialist and cross-verification expert(QA). all section integrationto persuasioncapability final proposal compositionand, clientanalysis-solution-price-differentiation between consistency cross-verification.
- `solution-architect`: proposal solution designspecialist. client requirements technical/service composition designand, implementation plan, schedule, deliverable, quality report approach establish.

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

- `.agents/skills/roi-calculator/SKILL.md`
- `.agents/skills/win-theme-builder/SKILL.md`
