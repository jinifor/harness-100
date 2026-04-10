---
name: comic-creator
description: >-
  Trigger when: the user wants the `comic-creator` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Comic Creator Harness

A harness where an agent team collaborates to produce comics — from storyboarding through dialogue, image generation, and editing — for formats ranging from 4-panel strips to long-form series.

## Specialist Agents

- `comic-editor`: Comic editor. Handles speech bubble placement, sound effect layering, final page layout, and reading flow optimization. Creates detailed editing specifications that can be directly applied in design/editing tools.
- `dialogue-writer`: Comic dialogue writer. Writes dialogue in each character's unique voice, and produces dialogue scripts including sound effects (onomatopoeia), narration, and speech bubble instructions.
- `image-generator`: Comic image generator. Uses AI image generation (Gemini) to produce panel images based on the storyboard. Maintains character consistency and art style uniformity.
- `quality-reviewer`: Comic quality reviewer (QA). Cross-validates consistency across story, dialogue, images, and editing. Identifies narrative continuity issues, character inconsistencies, and reading flow problems.
- `storyboarder`: Comic storyboarder. Develops synopses, breaks scenes into panels, designs panel layouts, and creates storyboards. Designs visual narrative structures specific to comics, from 4-panel strips to long-form series.

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
- `01_storyboard.md` — Storyboard
- `02_dialogue.md` — Dialogue script
- `03_image_prompts.md` — Image generation prompts and results
- `04_layout.md` — Page layout / editing specification
- `05_review_report.md` — Review report
- `panels/` — Generated panel images

## Extension Skills

- `.agents/skills/character-design-system/SKILL.md`
- `.agents/skills/panel-composition/SKILL.md`
- `.agents/skills/visual-narrative/SKILL.md`
