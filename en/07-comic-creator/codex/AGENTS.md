# Comic Creator Harness

This folder is the Codex version of the Comic Creator Harness. Start with the local `comic-creator` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/comic-creator/SKILL.md`
- Specialist agents: `.codex/agents/comic-editor.toml`, `.codex/agents/dialogue-writer.toml`, `.codex/agents/image-generator.toml`, `.codex/agents/quality-reviewer.toml`, `.codex/agents/storyboarder.toml`
- Extension skills: `.agents/skills/character-design-system/SKILL.md`, `.agents/skills/panel-composition/SKILL.md`, `.agents/skills/visual-narrative/SKILL.md`

## Workflow

- Start full-pipeline work with `comic-creator`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce comics — from storyboarding through dialogue, image generation, and editing — for formats ranging from 4-panel strips to long-form series.

## Deliverables

- `00_input.md` — Organized user input
- `01_storyboard.md` — Storyboard
- `02_dialogue.md` — Dialogue script
- `03_image_prompts.md` — Image generation prompts and results
- `04_layout.md` — Page layout / editing specification
- `05_review_report.md` — Review report
- `panels/` — Generated panel images
