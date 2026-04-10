# Advertising Campaign Harness

This folder is the Codex version of the Advertising Campaign Harness. Start with the local `advertising-campaign` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/advertising-campaign/SKILL.md`
- Specialist agents: `.codex/agents/campaign-reviewer.toml`, `.codex/agents/copywriter.toml`, `.codex/agents/creative-director.toml`, `.codex/agents/market-analyst.toml`, `.codex/agents/media-planner.toml`
- Extension skills: `.agents/skills/ad-copywriting-formulas/SKILL.md`, `.agents/skills/media-mix-calculator/SKILL.md`

## Workflow

- Start full-pipeline work with `advertising-campaign`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to design advertising campaigns: target analysis, copy, creative, and media plans.

## Deliverables

- `00_input.md` — Organized user input
- `01_market_analysis.md` — Market/target analysis report
- `02_ad_copy.md` — Ad copy set
- `03_creative_concept.md` — Creative concept/storyboards
- `04_media_plan.md` — Media plan
- `05_review_report.md` — Review report
