---
name: ecommerce-launcher
description: >-
  Trigger when: the user wants the `ecommerce-launcher` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# E-commerce Launcher Harness

An e-commerce launch harness. An agent team collaborates to produce product planning, product detail pages, pricing strategy, marketing plans, and customer service architecture for online store launches.

## Specialist Agents

- `cs-architect`: E-commerce CS architect. Designs FAQ, response manuals, return/exchange policies, VOC collection systems, and escalation processes to complete CS infrastructure before launch.
- `detail-page-writer`: E-commerce detail page writer. Creates product detail page copy designed to maximize purchase conversion, based on the product planning brief. Includes headline copy, content structure, SEO, and persuasion logic.
- `marketing-manager`: E-commerce marketing manager. Designs launch campaigns, channel-specific advertising strategies, content marketing, influencer collaborations, and performance marketing KPIs.
- `pricing-strategist`: E-commerce pricing strategist. Develops cost analysis, competitive pricing research, margin design, promotional pricing, and bundle strategies to achieve both profitability and competitiveness.
- `product-planner`: E-commerce product planner. Conducts market research, target customer analysis, competitive benchmarking, product positioning, and USP development.

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

- `.agents/skills/conversion-optimization/SKILL.md`
- `.agents/skills/product-copy-formulas/SKILL.md`
