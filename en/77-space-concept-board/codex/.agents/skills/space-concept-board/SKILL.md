---
name: space-concept-board
description: >-
  Trigger when: the user wants the `space-concept-board` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Space Concept Board Harness

A harness where an agent team collaborates to generate style analysis, moodboard, color palette, furniture/accessory list, budget sheet, and shopping guide for an interior space concept board.

## Specialist Agents

- `budget-manager`: Budget manager. Creates a budget sheet based on the item list and provides prioritized purchasing strategies and a shopping guide.
- `concept-reviewer`: Concept reviewer (QA). Cross-verifies consistency across style analysis, moodboard, item list, and budget sheet, and evaluates practicality, aesthetics, and budget alignment.
- `item-curator`: Item curator. Selects furniture and accessories that match the moodboard and style, proposes spatial layouts, and researches vendors and alternative products.
- `moodboard-designer`: Moodboard designer. Based on style analysis results, composes a color palette, texture/material board, and spatial atmosphere guide as a cohesive visual language.
- `style-analyst`: Space style analyst. Analyzes the user's spatial conditions, lifestyle, and preferences to diagnose the optimal interior style and collects reference images and case studies.

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
- `01_style_analysis.md` — Style analysis report
- `02_moodboard.md` — Moodboard + color palette
- `03_item_list.md` — Furniture/accessory list + layout suggestions
- `04_budget_shopping.md` — Budget sheet + shopping guide
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/color-harmony-engine/SKILL.md`
- `.agents/skills/spatial-layout-guide/SKILL.md`
