---
name: game-narrative
description: >-
  Trigger when: the user wants the `game-narrative` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Game Narrative Harness

A harness where an agent team collaborates to design game story, quests, dialogue, and branching scenarios.

## Specialist Agents

- `branch-architect`: Game branch architect. Designs story branching structures, ending variations, flag systems, and consequence frameworks.
- `dialogue-writer`: Game dialogue writer. Writes NPC dialogue, player choices, emotional direction, and cutscene dialogue tailored to each character's personality.
- `narrative-reviewer`: Game narrative reviewer (QA). Cross-validates consistency, plot holes, and balance across world-building, quests, dialogue, and branches.
- `quest-designer`: Game quest designer. Designs main/side quests and concretely defines objectives, steps, rewards, and failure conditions.
- `worldbuilder`: Game world designer. Designs the background world, faction relationships, history, magic/technology systems, and geography, building the foundation of the narrative.

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
- `01_worldbuilding.md` — World-building document
- `02_quest_design.md` — Quest design document
- `03_dialogue_script.md` — Dialogue script
- `04_branch_map.md` — Branching structure map
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/branching-logic/SKILL.md`
- `.agents/skills/dialogue-systems/SKILL.md`
- `.agents/skills/quest-design-patterns/SKILL.md`
