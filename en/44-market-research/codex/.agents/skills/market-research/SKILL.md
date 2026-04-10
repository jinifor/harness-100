---
name: market-research
description: >-
  Trigger when: the user wants the `market-research` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Market Research Harness

Market research: a harness where an agent team collaborates to perform industry analysis → competitor analysis → consumer analysis → trend analysis → research review.

## Specialist Agents

- `competitor-analyst`: Competitive analyst. Performs competitor mapping, strategic group analysis, SWOT analysis, positioning map creation, and competitive advantage identification.
- `consumer-analyst`: Consumer analyst. Performs customer segmentation, purchase journey mapping, needs analysis, persona design, and research methodology proposals.
- `industry-analyst`: Industry analyst. Performs market size and growth rate estimation, value chain analysis, industry structure (Porter's 5 Forces), and regulatory environment analysis.
- `research-reviewer`: Research reviewer (QA). Cross-validates consistency across industry, competitive, consumer, and trend analyses. Integrates insights and derives strategic recommendations.
- `trend-analyst`: Trend analyst. Performs macro environment (PESTLE), micro trend, technology trend, scenario analysis, and future outlook assessments.

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

- `.agents/skills/porter-five-forces/SKILL.md`
- `.agents/skills/tam-sam-som-calculator/SKILL.md`
