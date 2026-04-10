# Thesis Advisor Harness

This folder is the Codex version of the Thesis Advisor Harness. Start with the local `thesis-advisor` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/thesis-advisor/SKILL.md`
- Specialist agents: `.codex/agents/literature-analyst.toml`, `.codex/agents/methodology-expert.toml`, `.codex/agents/proofreader.toml`, `.codex/agents/topic-explorer.toml`, `.codex/agents/writing-coach.toml`
- Extension skills: `.agents/skills/academic-writing-style/SKILL.md`, `.agents/skills/research-methodology/SKILL.md`

## Workflow

- Start full-pipeline work with `thesis-advisor`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for thesis writing: topic selection, literature review, methodology, writing, and proofreading.

## Deliverables

- `00_input.md` — Organized user input
- `01_topic_exploration.md` — Topic exploration report
- `02_literature_review.md` — Literature analysis report
- `03_methodology.md` — Methodology design document
- `04_writing_guide.md` — Writing guide
- `05_proofreading.md` — Proofreading report
- `06_review_report.md` — Review report
