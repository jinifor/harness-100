---
name: visual-storytelling
description: >-
  Trigger when: the user wants the `visual-storytelling` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Visual Storytelling Harness

A harness where an agent team collaborates to produce visual storytelling: story design, text writing, AI image generation, HTML layout, and integrated editing.

## Specialist Agents

- `editorial-reviewer`: Editorial reviewer (QA). Cross-validates consistency across story, text, images, and layout, verifying the quality of narrative flow, emotional consistency, and visual unity.
- `essay-writer`: Essay writer. Writes the text portion of visual storytelling. Composes body text, captions, quotes, and dialogue in an emotional style that breathes in sync with images scene by scene.
- `image-prompter`: Image . Gemini Image utilization Visual Storyof Scenein Image generate. Scene between Visual Consistency Prompt design.
- `layout-builder`: Layout . Textand Image Integration HTML/CSS Visual Story page produce. Responsive , Typography, design.
- `story-architect`: Story Design. Visual Storytellingof Narrative Structure, Scene composition, visual-Text Balance design. Scene Imageand Textof combinationto of narrative photography .

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
- `01_story_blueprint.md` — Story blueprint
- `02_essay_text.md` — Essay body text
- `03_image_prompts.md` — Image prompt sheet
- `04_layout.html` — HTML layout
- `05_review_report.md` — Editorial review report
- `images/` — Generated images directory

## Extension Skills

- `.agents/skills/image-prompt-engineering/SKILL.md`
- `.agents/skills/narrative-structure-patterns/SKILL.md`
