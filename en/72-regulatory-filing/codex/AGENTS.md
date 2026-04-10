# Regulatory Filing Harness

This folder is the Codex version of the Regulatory Filing Harness. Start with the local `regulatory-filing` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/regulatory-filing/SKILL.md`
- Specialist agents: `.codex/agents/attachment-preparer.toml`, `.codex/agents/document-drafter.toml`, `.codex/agents/requirements-investigator.toml`, `.codex/agents/submission-verifier.toml`
- Extension skills: `.agents/skills/form-filling-guide/SKILL.md`, `.agents/skills/permit-requirements-db/SKILL.md`

## Workflow

- Start full-pipeline work with `regulatory-filing`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A regulatory filing and permit application agent team harness.
