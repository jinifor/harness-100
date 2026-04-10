---
name: sustainability-audit
description: >-
  Trigger when: the user wants the `sustainability-audit` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Sustainability Audit Harness

A sustainability audit harness. An agent team collaborates to produce environmental analysis, social assessment, governance review, ESG reporting, and improvement planning.

## Specialist Agents

- `environmental-analyst`: ESG environmental analyst. Assesses carbon emissions calculation, energy efficiency, waste management, water resource usage, and biodiversity impact.
- `esg-reporter`: ESG report writer. Compiles environmental, social, and governance assessment results into an integrated ESG report aligned with international frameworks such as GRI, SASB, and TCFD.
- `governance-reviewer`: ESG governance reviewer. Reviews board structure, corporate ethics, compliance, risk management, information disclosure, and anti-corruption frameworks.
- `improvement-planner`: ESG improvement planner. Analyzes weaknesses across E/S/G pillars and develops prioritized improvement roadmaps, KPIs, and investment plans.
- `social-assessor`: ESG social impact assessor. Evaluates labor practices, human rights, diversity and inclusion, community contribution, and supply chain social responsibility.

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

- `.agents/skills/ghg-protocol/SKILL.md`
- `.agents/skills/materiality-assessment/SKILL.md`
