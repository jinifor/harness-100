# Service Legal Docs Harness

This folder is the Codex version of the Service Legal Docs Harness. Start with the local `service-legal-docs` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/service-legal-docs/SKILL.md`
- Specialist agents: `.codex/agents/consistency-reviewer.toml`, `.codex/agents/consumer-analyst.toml`, `.codex/agents/privacy-specialist.toml`, `.codex/agents/tos-specialist.toml`
- Extension skills: `.agents/skills/cross-document-linker/SKILL.md`, `.agents/skills/unfair-terms-detector/SKILL.md`

## Workflow

- Start full-pipeline work with `service-legal-docs`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A service terms and legal document drafting agent team harness.
