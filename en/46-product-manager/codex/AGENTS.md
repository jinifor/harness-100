# Product Manager Harness

This folder is the Codex version of the Product Manager Harness. Start with the local `product-manager` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/product-manager/SKILL.md`
- Specialist agents: `.codex/agents/pm-reviewer.toml`, `.codex/agents/prd-writer.toml`, `.codex/agents/sprint-planner.toml`, `.codex/agents/story-writer.toml`, `.codex/agents/strategist.toml`
- Extension skills: `.agents/skills/rice-prioritizer/SKILL.md`, `.agents/skills/story-point-estimator/SKILL.md`

## Workflow

- Start full-pipeline work with `product-manager`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to generate the full PM workflow: Roadmap, PRD, User Stories, Sprint Plan, and Retrospective.

## Deliverables

- `00_input.md` — Organized user input
- `01_product_roadmap.md` — Product roadmap
- `02_prd.md` — Product requirements document
- `03_user_stories.md` — User story list
- `04_sprint_plan.md` — Sprint plan
- `05_review_report.md` — PM review report
