# Personal Branding Harness

This folder is the Codex version of the Personal Branding Harness. Start with the local `personal-branding` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/personal-branding/SKILL.md`
- Specialist agents: `.codex/agents/cover-letter-writer.toml`, `.codex/agents/portfolio-designer.toml`, `.codex/agents/positioning-strategist.toml`, `.codex/agents/profile-optimizer.toml`, `.codex/agents/resume-writer.toml`
- Extension skills: `.agents/skills/ats-optimizer/SKILL.md`, `.agents/skills/linkedin-seo/SKILL.md`

## Workflow

- Start full-pipeline work with `personal-branding`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A personal branding agent team harness.
