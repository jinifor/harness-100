# Hiring Pipeline Harness

This folder is the Codex version of the Hiring Pipeline Harness. Start with the local `hiring-pipeline` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/hiring-pipeline/SKILL.md`
- Specialist agents: `.codex/agents/interview-designer.toml`, `.codex/agents/jd-writer.toml`, `.codex/agents/offer-coordinator.toml`, `.codex/agents/screening-expert.toml`, `.codex/agents/sourcing-specialist.toml`
- Extension skills: `.agents/skills/competency-model/SKILL.md`, `.agents/skills/interview-scorecard/SKILL.md`

## Workflow

- Start full-pipeline work with `hiring-pipeline`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- hiring process: JDwriting→sourcing→screening→interview→assessment→offerto A harness where an agent team collaborates to produce deliverables.
