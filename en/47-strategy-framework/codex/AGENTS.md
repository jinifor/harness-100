# Strategy Framework Harness

This folder is the Codex version of the Strategy Framework Harness. Start with the local `strategy-framework` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/strategy-framework/SKILL.md`
- Specialist agents: `.codex/agents/bsc-analyst.toml`, `.codex/agents/okr-designer.toml`, `.codex/agents/strategy-reviewer.toml`, `.codex/agents/strategy-writer.toml`, `.codex/agents/swot-specialist.toml`
- Extension skills: `.agents/skills/okr-quality-checker/SKILL.md`, `.agents/skills/tows-matrix-builder/SKILL.md`

## Workflow

- Start full-pipeline work with `strategy-framework`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to generate an organizational strategy framework in sequence: OKR Design, BSC Mapping, SWOT Analysis, Vision & Mission Statement, and Strategy Execution Roadmap.

## Deliverables

- `00_input.md` — Organized user input
- `01_okr_design.md` — OKR design document
- `02_bsc_mapping.md` — BSC mapping table
- `03_swot_analysis.md` — SWOT analysis report
- `04_vision_mission.md` — Vision & mission statement
- `05_strategy_roadmap.md` — Strategy execution roadmap
- `06_review_report.md` — Review report
