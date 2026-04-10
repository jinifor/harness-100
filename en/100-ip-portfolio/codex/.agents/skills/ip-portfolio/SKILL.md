---
name: ip-portfolio
description: >-
  Trigger when: the user wants the `ip-portfolio` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# IP Portfolio Harness

An intellectual property portfolio management harness. An agent team collaborates to produce IP analysis, patent mapping, protection strategy, licensing strategy, and renewal scheduling.

## Specialist Agents

- `ip-analyst`: IP analyst. Assesses the organization's intellectual property portfolio, evaluates IP asset value, and creates strategic portfolio maps.
- `license-strategist`: IP license strategist. Develops IP asset monetization strategies, cross-licensing, technology transfer, and open source strategies, and designs license agreement terms.
- `patent-mapper`: Patent, trademark, and copyright mapper. Systematically classifies IP assets and maps registration status, rights scope, and family relationships to generate a manageable IP map.
- `protection-advisor`: IP protection strategy advisor. Develops infringement monitoring, defense strategies, dispute response, and protection enhancement measures, and produces a comprehensive protection strategy report.
- `renewal-scheduler`: IP renewal schedule manager. Manages patent annuity, trademark renewal, and design renewal deadlines, calculates costs, and supports retention/abandonment decision-making.

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

- `.agents/skills/ip-landscape-analysis/SKILL.md`
- `.agents/skills/patent-valuation/SKILL.md`
