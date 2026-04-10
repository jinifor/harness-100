# Presentation Designer Harness

This folder is the Codex version of the Presentation Designer Harness. Start with the local `presentation-designer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/presentation-designer/SKILL.md`
- Specialist agents: `.codex/agents/deck-reviewer.toml`, `.codex/agents/info-architect.toml`, `.codex/agents/presentation-coach.toml`, `.codex/agents/storyteller.toml`, `.codex/agents/visual-designer.toml`
- Extension skills: `.agents/skills/data-visualization-guide/SKILL.md`, `.agents/skills/slide-layout-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `presentation-designer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce presentations: planning, storyboards, slides, and speaker notes.

## Deliverables

- `00_input.md` — Organized user input
- `01_story_structure.md` — Story structure/message map
- `02_info_design.md` — Information design/data visualization guide
- `03_slide_deck.md` — Slide deck (markdown-based)
- `04_speaker_notes.md` — Speaker notes/timing/Q&A
- `05_review_report.md` — Review report
