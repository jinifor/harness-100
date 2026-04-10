# Space Concept Board Harness

This folder is the Codex version of the Space Concept Board Harness. Start with the local `space-concept-board` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/space-concept-board/SKILL.md`
- Specialist agents: `.codex/agents/budget-manager.toml`, `.codex/agents/concept-reviewer.toml`, `.codex/agents/item-curator.toml`, `.codex/agents/moodboard-designer.toml`, `.codex/agents/style-analyst.toml`
- Extension skills: `.agents/skills/color-harmony-engine/SKILL.md`, `.agents/skills/spatial-layout-guide/SKILL.md`

## Workflow

- Start full-pipeline work with `space-concept-board`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to generate style analysis, moodboard, color palette, furniture/accessory list, budget sheet, and shopping guide for an interior space concept board.

## Deliverables

- `00_input.md` — Organized user input
- `01_style_analysis.md` — Style analysis report
- `02_moodboard.md` — Moodboard + color palette
- `03_item_list.md` — Furniture/accessory list + layout suggestions
- `04_budget_shopping.md` — Budget sheet + shopping guide
- `05_review_report.md` — Review report
