# SOP Writer Harness

This folder is the Codex version of the SOP Writer Harness. Start with the local `sop-writer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/sop-writer/SKILL.md`
- Specialist agents: `.codex/agents/checklist-designer.toml`, `.codex/agents/procedure-writer.toml`, `.codex/agents/process-analyst.toml`, `.codex/agents/training-developer.toml`, `.codex/agents/version-controller.toml`
- Extension skills: `.agents/skills/checklist-design/SKILL.md`, `.agents/skills/process-mapping/SKILL.md`

## Workflow

- Start full-pipeline work with `sop-writer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- standard operating procedure(SOP) processanalysis→procedure document→checklist→training materials→versionmanagement A harness where an agent team collaborates to produce deliverables.
