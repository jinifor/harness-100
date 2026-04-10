---
name: startup-launcher
description: >-
  Trigger when: the user wants the `startup-launcher` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Startup Launcher Harness

Startup launch planning: a harness where an agent team collaborates to perform market analysis → business modeling → MVP architecture → pitch deck creation → launch review.

## Specialist Agents

- `business-modeler`: Business modeler. Creates Business Model Canvas, designs revenue models, performs unit economics analysis, and builds financial projections.
- `launch-reviewer`: Launch reviewer (QA). Cross-validates logical consistency between market analysis, business model, MVP, and pitch deck. Assesses investment readiness and execution feasibility.
- `market-analyst`: Startup market analyst. Performs idea validation, market sizing (TAM/SAM/SOM), competitive analysis, customer persona definition, and PMF hypothesis formulation.
- `mvp-architect`: MVP architect. Performs core feature prioritization, technology stack selection, development roadmap creation, and user flow design.
- `pitch-creator`: Pitch deck creator. Designs investor presentation storylines, slide structures, and core narratives.

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

- `.agents/skills/pitch-deck-framework/SKILL.md`
- `.agents/skills/unit-economics-calculator/SKILL.md`
