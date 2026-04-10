# Public Speaking Harness

This folder is the Codex version of the Public Speaking Harness. Start with the local `public-speaking` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/public-speaking/SKILL.md`
- Specialist agents: `.codex/agents/audience-analyst.toml`, `.codex/agents/debate-preparer.toml`, `.codex/agents/qa-strategist.toml`, `.codex/agents/rehearsal-coach.toml`, `.codex/agents/speech-writer.toml`
- Extension skills: `.agents/skills/audience-engagement/SKILL.md`, `.agents/skills/rhetoric-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `public-speaking`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- comprehensive speechdocument→presentationversus→debatepreparationfrom→Q&Aexpectedanswer→rehearsalguide A harness where an agent team collaborates to produce deliverables.
