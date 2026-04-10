# Visual Storytelling Harness

This folder is the Codex version of the Visual Storytelling Harness. Start with the local `visual-storytelling` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/visual-storytelling/SKILL.md`
- Specialist agents: `.codex/agents/editorial-reviewer.toml`, `.codex/agents/essay-writer.toml`, `.codex/agents/image-prompter.toml`, `.codex/agents/layout-builder.toml`, `.codex/agents/story-architect.toml`
- Extension skills: `.agents/skills/image-prompt-engineering/SKILL.md`, `.agents/skills/narrative-structure-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `visual-storytelling`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce visual storytelling: story design, text writing, AI image generation, HTML layout, and integrated editing.

## Deliverables

- `00_input.md` — Organized user input
- `01_story_blueprint.md` — Story blueprint
- `02_essay_text.md` — Essay body text
- `03_image_prompts.md` — Image prompt sheet
- `04_layout.html` — HTML layout
- `05_review_report.md` — Editorial review report
- `images/` — Generated images directory
