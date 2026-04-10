---
name: real-estate-analyst
description: >-
  Trigger when: the user wants the `real-estate-analyst` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Real Estate Analyst Harness

A real estate analysis harness. An agent team collaborates to produce market research, location analysis, profitability analysis, risk assessment, and investment reports.

## Specialist Agents

- `location-analyst`: Location analysis expert. Evaluates location competitiveness by analyzing transit access, school districts, commercial areas, amenities, development catalysts, and natural environment from multiple angles.
- `market-researcher`: Real estate market research expert. Analyzes the market environment by researching macroeconomic indicators, regional real estate market trends, supply/demand analysis, price trends, and policy changes.
- `profitability-analyst`: Profitability analysis expert. Precisely analyzes financial returns of real estate investment including rental yields, capital gains, cash flow, leverage effects, IRR, and NPV.
- `report-writer`: Investment report writing expert. Synthesizes market research, location analysis, profitability, and risk analysis results to produce reports with investment opinions, scenario-based return comparisons, and final investment recommendations.
- `risk-assessor`: Real estate risk assessment expert. Comprehensively evaluates regulatory, market, liquidity, structural/physical, and legal risks and develops risk response strategies.

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

- `.agents/skills/cap-rate-calculator/SKILL.md`
- `.agents/skills/location-scoring/SKILL.md`
