# Travel Planner Harness

This folder is the Codex version of the Travel Planner Harness. Start with the local `travel-planner` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/travel-planner/SKILL.md`
- Specialist agents: `.codex/agents/budget-manager.toml`, `.codex/agents/destination-analyst.toml`, `.codex/agents/itinerary-designer.toml`, `.codex/agents/local-guide.toml`
- Extension skills: `.agents/skills/budget-calculator/SKILL.md`, `.agents/skills/route-optimizer/SKILL.md`

## Workflow

- Start full-pipeline work with `travel-planner`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to generate destination analysis, itinerary, accommodation, budget, and local information for travel planning.

## Deliverables

- `00_input.md` — Organized user input
- `01_destination_analysis.md` — Destination analysis report
- `02_itinerary.md` — Itinerary
- `03_accommodation.md` — Accommodation guide
- `04_budget.md` — Budget plan
- `05_local_guide.md` — Local information guide
