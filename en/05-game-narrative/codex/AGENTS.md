# Game Narrative Harness

This folder is the Codex version of the Game Narrative Harness. Start with the local `game-narrative` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/game-narrative/SKILL.md`
- Specialist agents: `.codex/agents/branch-architect.toml`, `.codex/agents/dialogue-writer.toml`, `.codex/agents/narrative-reviewer.toml`, `.codex/agents/quest-designer.toml`, `.codex/agents/worldbuilder.toml`
- Extension skills: `.agents/skills/branching-logic/SKILL.md`, `.agents/skills/dialogue-systems/SKILL.md`, `.agents/skills/quest-design-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `game-narrative`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to design game story, quests, dialogue, and branching scenarios.

## Deliverables

- `00_input.md` — Organized user input
- `01_worldbuilding.md` — World-building document
- `02_quest_design.md` — Quest design document
- `03_dialogue_script.md` — Dialogue script
- `04_branch_map.md` — Branching structure map
- `05_review_report.md` — Review report
