---
name: advertising-campaign
description: >-
  Trigger when: the user wants the `advertising-campaign` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Advertising Campaign Harness

A harness where an agent team collaborates to design advertising campaigns: target analysis, copy, creative, and media plans.

## Specialist Agents

- `campaign-reviewer`: Campaign reviewer (QA). Cross-validates consistency across market analysis, copy, creative, and media plans, identifying gaps, contradictions, and quality issues to provide feedback.
- `copywriter`: Advertising copywriter. Writes ad copy across all campaign channels including headlines, body copy, CTAs, and slogans based on target analysis.
- `creative-director`: Creative director. Designs visual concepts for advertising campaigns, writes storyboards, and creates ad visual drafts using Gemini image generation.
- `market-analyst`: Advertising campaign market/target analyst. Segments the target audience for products/services, analyzes competitive advertising, and derives insights that form the foundation of campaign strategy.
- `media-planner`: Media planner. Designs optimal media mixes according to campaign goals and budget, establishing per-channel budget allocation, scheduling, and KPIs.

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
- `01_market_analysis.md` — Market/target analysis report
- `02_ad_copy.md` — Ad copy set
- `03_creative_concept.md` — Creative concept/storyboards
- `04_media_plan.md` — Media plan
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/ad-copywriting-formulas/SKILL.md`
- `.agents/skills/media-mix-calculator/SKILL.md`
