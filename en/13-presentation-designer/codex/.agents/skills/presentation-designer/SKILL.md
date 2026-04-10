---
name: presentation-designer
description: >-
  Trigger when: the user wants the `presentation-designer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Presentation Designer Harness

A harness where an agent team collaborates to produce presentations: planning, storyboards, slides, and speaker notes.

## Specialist Agents

- `deck-reviewer`: Deck reviewer (QA). Cross-validates consistency across story, information design, visuals, and speaker notes, identifying gaps, contradictions, and quality issues to provide feedback.
- `info-architect`: Information architect. Selects charts/graphs/diagrams for effective data visualization and structures complex information into audience-friendly formats.
- `presentation-coach`: Presentation coach. Provides slide-by-slide speaker notes, timing allocation, audience engagement strategies, anticipated Q&A responses, and rehearsal guides.
- `storyteller`: Presentation storyteller. Defines the presentation's core message based on audience analysis and designs the logical flow and emotion curve.
- `visual-designer`: Visual designer. Designs presentation slide layouts, colors, typography, and images, and produces markdown-based slide decks.

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
- `01_story_structure.md` — Story structure/message map
- `02_info_design.md` — Information design/data visualization guide
- `03_slide_deck.md` — Slide deck (markdown-based)
- `04_speaker_notes.md` — Speaker notes/timing/Q&A
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/data-visualization-guide/SKILL.md`
- `.agents/skills/slide-layout-patterns/SKILL.md`
