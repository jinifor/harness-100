# Documentary Research Harness

This folder is the Codex version of the Documentary Research Harness. Start with the local `documentary-research` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/documentary-research/SKILL.md`
- Specialist agents: `.codex/agents/fact-checker.toml`, `.codex/agents/interviewer.toml`, `.codex/agents/narrator.toml`, `.codex/agents/researcher.toml`, `.codex/agents/story-architect.toml`
- Extension skills: `.agents/skills/interview-design/SKILL.md`, `.agents/skills/investigative-research/SKILL.md`, `.agents/skills/narrative-structure/SKILL.md`

## Workflow

- Start full-pipeline work with `documentary-research`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce documentary research, treatment plans, interview questions, and narration scripts.

## Deliverables

- `00_input.md` — Organized user input
- `01_research_brief.md` — Research brief
- `02_structure.md` — Treatment/structure design
- `03_interview_guide.md` — Interview guide
- `04_narration_script.md` — Narration script
- `05_review_report.md` — Fact-check/review report
