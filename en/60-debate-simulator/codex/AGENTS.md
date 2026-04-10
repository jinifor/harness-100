# Debate Simulator Harness

This folder is the Codex version of the Debate Simulator Harness. Start with the local `debate-simulator` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/debate-simulator/SKILL.md`
- Specialist agents: `.codex/agents/con-debater.toml`, `.codex/agents/judge.toml`, `.codex/agents/pro-debater.toml`, `.codex/agents/rapporteur.toml`, `.codex/agents/topic-analyst.toml`
- Extension skills: `.agents/skills/argumentation-framework/SKILL.md`, `.agents/skills/logical-fallacy-detector/SKILL.md`

## Workflow

- Start full-pipeline work with `debate-simulator`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for debate simulation.

## Deliverables

- `00_input.md` — Organized user input
- `01_topic_analysis.md` — Topic analysis
- `02_pro_arguments.md` — Pro-side arguments
- `03_con_arguments.md` — Con-side arguments
- `04_verdict.md` — Verdict
- `05_debate_record.md` — Debate record
- `06_review_report.md` — Review report
