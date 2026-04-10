---
name: travel-planner
description: >-
  Trigger when: the user wants the `travel-planner` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Travel Planner Harness

A harness where an agent team collaborates to generate destination analysis, itinerary, accommodation, budget, and local information for travel planning.

## Specialist Agents

- `budget-manager`: Travel budget management expert. Calculates overall travel budget including flights, accommodation, meals, transport, sightseeing, and shopping, and designs optimal allocation within budget constraints.
- `destination-analyst`: Destination analysis expert. Comprehensively analyzes tourism resources, optimal visiting seasons, visa/entry requirements, and safety information to lay the groundwork for travel planning.
- `itinerary-designer`: Itinerary design expert. Designs efficient daily detailed itineraries based on destination analysis, optimizing time allocation and travel routes.
- `local-guide`: Local information guide. Provides comprehensive practical information needed on-site, including transport usage, restaurants, cultural etiquette, useful apps, and emergency contacts.

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
- `01_destination_analysis.md` — Destination analysis report
- `02_itinerary.md` — Itinerary
- `03_accommodation.md` — Accommodation guide
- `04_budget.md` — Budget plan
- `05_local_guide.md` — Local information guide

## Extension Skills

- `.agents/skills/budget-calculator/SKILL.md`
- `.agents/skills/route-optimizer/SKILL.md`
