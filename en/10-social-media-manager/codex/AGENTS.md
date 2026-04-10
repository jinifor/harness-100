# Social Media Manager Harness

This folder is the Codex version of the Social Media Manager Harness. Start with the local `social-media-manager` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/social-media-manager/SKILL.md`
- Specialist agents: `.codex/agents/copywriter.toml`, `.codex/agents/hashtag-analyst.toml`, `.codex/agents/performance-reviewer.toml`, `.codex/agents/sns-strategist.toml`, `.codex/agents/visual-planner.toml`
- Extension skills: `.agents/skills/hashtag-science/SKILL.md`, `.agents/skills/platform-algorithms/SKILL.md`, `.agents/skills/viral-copywriting/SKILL.md`

## Workflow

- Start full-pipeline work with `social-media-manager`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce SNS content calendars, post copy, hashtags, and performance analysis.

## Deliverables

- `00_input.md` — Organized user input
- `01_strategy.md` — SNS strategy/content calendar
- `02_posts.md` — Post copy collection
- `03_visuals.md` — Visual plan
- `04_hashtags.md` — Hashtag strategy
- `05_review_report.md` — Review report
