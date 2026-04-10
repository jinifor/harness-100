---
name: product-manager
description: >-
  Trigger when: the user wants the `product-manager` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Product Manager Harness

A harness where an agent team collaborates to generate the full PM workflow: Roadmap, PRD, User Stories, Sprint Plan, and Retrospective.

## Specialist Agents

- `pm-reviewer`: PM Reviewer (QA). Cross-validates consistency, feasibility, and gaps across the roadmap, PRD, user stories, and sprint plan.
- `prd-writer`: PRD Writer. Authors the product requirements document, defining exactly what the engineering and design teams need to build.
- `sprint-planner`: Sprint Planner. Calculates team capacity, sets sprint goals, allocates stories, manages risks, and designs retrospective templates.
- `story-writer`: Story Writer. Creates development-ready user stories from the PRD, including story maps, acceptance criteria (AC), and story points.
- `strategist`: Product Strategist. Defines product vision, sets goals, builds roadmaps, operates prioritization frameworks, and establishes OKRs.

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
- `01_product_roadmap.md` — Product roadmap
- `02_prd.md` — Product requirements document
- `03_user_stories.md` — User story list
- `04_sprint_plan.md` — Sprint plan
- `05_review_report.md` — PM review report

## Extension Skills

- `.agents/skills/rice-prioritizer/SKILL.md`
- `.agents/skills/story-point-estimator/SKILL.md`
