# IP Portfolio Harness

This folder is the Codex version of the IP Portfolio Harness. Start with the local `ip-portfolio` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/ip-portfolio/SKILL.md`
- Specialist agents: `.codex/agents/ip-analyst.toml`, `.codex/agents/license-strategist.toml`, `.codex/agents/patent-mapper.toml`, `.codex/agents/protection-advisor.toml`, `.codex/agents/renewal-scheduler.toml`
- Extension skills: `.agents/skills/ip-landscape-analysis/SKILL.md`, `.agents/skills/patent-valuation/SKILL.md`

## Workflow

- Start full-pipeline work with `ip-portfolio`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An intellectual property portfolio management harness. An agent team collaborates to produce IP analysis, patent mapping, protection strategy, licensing strategy, and renewal scheduling.
