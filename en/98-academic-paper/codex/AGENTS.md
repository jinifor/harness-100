# Academic Paper Harness

This folder is the Codex version of the Academic Paper Harness. Start with the local `academic-paper` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/academic-paper/SKILL.md`
- Specialist agents: `.codex/agents/experiment-manager.toml`, `.codex/agents/paper-writer.toml`, `.codex/agents/research-designer.toml`, `.codex/agents/statistical-analyst.toml`, `.codex/agents/submission-preparer.toml`
- Extension skills: `.agents/skills/citation-standards/SKILL.md`, `.agents/skills/research-methodology/SKILL.md`

## Workflow

- Start full-pipeline work with `academic-paper`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An academic paper writing harness. An agent team collaborates to produce research design, experiment management, statistical analysis, paper writing, and submission preparation.
