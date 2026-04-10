---
name: side-project-launcher
description: >-
  Trigger when: the user wants the `side-project-launcher` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Side Project Launcher Harness

companyproject basis ideaverify→tech stack→MVP→developmentroadmap→launchchecklist A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `idea-validator`: idea verifyspecialist. companyproject idea marketnature, competition situation, differentiation point analysisand Go/No-Go judgment provide.
- `launch-reviewer`: launch reviewer(QA). idea-tech stack-MVP-roadmap between consistency cross-verificationand, execution possibleperformance risk comprehensive assessment.
- `mvp-designer`: MVP designspecialist. core feature definitionand, user and composition designand, implementation possibleKorean MVP writing.
- `roadmap-builder`: roadmap writingspecialist. MVP basedas development schedule, milestone, launch strategy, launch checklist establish.
- `techstack-analyst`: tech stack analysis. project requirements and developmentspecialist competency quality tech stack comparison·analysisand recommendation.

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

- `.agents/skills/market-sizing-calculator/SKILL.md`
- `.agents/skills/techstack-decision-matrix/SKILL.md`
