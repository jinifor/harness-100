# CLI Tool Builder Harness

This folder is the Codex version of the CLI Tool Builder Harness. Start with the local `cli-tool-builder` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/cli-tool-builder/SKILL.md`
- Specialist agents: `.codex/agents/command-designer.toml`, `.codex/agents/core-developer.toml`, `.codex/agents/docs-writer.toml`, `.codex/agents/release-engineer.toml`, `.codex/agents/test-engineer.toml`
- Extension skills: `.agents/skills/arg-parser-generator/SKILL.md`, `.agents/skills/ux-linter/SKILL.md`

## Workflow

- Start full-pipeline work with `cli-tool-builder`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- CLI tool construction: a harness where an agent team collaborates to perform command design → core development → testing → documentation → release.
