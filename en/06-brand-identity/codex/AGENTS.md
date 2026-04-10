# Brand Identity Harness

This folder is the Codex version of the Brand Identity Harness. Start with the local `brand-identity` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/brand-identity/SKILL.md`
- Specialist agents: `.codex/agents/brand-strategist.toml`, `.codex/agents/copywriter.toml`, `.codex/agents/identity-reviewer.toml`, `.codex/agents/naming-specialist.toml`, `.codex/agents/visual-director.toml`
- Extension skills: `.agents/skills/brand-archetype/SKILL.md`, `.agents/skills/color-psychology/SKILL.md`, `.agents/skills/naming-methodology/SKILL.md`

## Workflow

- Start full-pipeline work with `brand-identity`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to design brand identity from naming through slogans, tone and manner, and visual guidelines.

## Deliverables

- `00_input.md` — Organized user input
- `01_brand_strategy.md` — Brand strategy report
- `02_naming_candidates.md` — Naming candidates
- `03_verbal_identity.md` — Verbal identity (slogans, tone and manner)
- `04_visual_identity.md` — Visual identity (color, typography, logo)
- `05_review_report.md` — Review report
