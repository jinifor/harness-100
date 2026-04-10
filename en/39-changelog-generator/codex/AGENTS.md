# Changelog Generator Harness

This folder is the Codex version of the Changelog Generator Harness. Start with the local `changelog-generator` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/changelog-generator/SKILL.md`
- Specialist agents: `.codex/agents/announcement-writer.toml`, `.codex/agents/change-classifier.toml`, `.codex/agents/commit-analyst.toml`, `.codex/agents/migration-guide-writer.toml`, `.codex/agents/release-note-writer.toml`
- Extension skills: `.agents/skills/commit-parser/SKILL.md`, `.agents/skills/semver-analyzer/SKILL.md`

## Workflow

- Start full-pipeline work with `changelog-generator`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Changelog generation: a harness where an agent team collaborates to perform commit analysis → change classification → release note writing → migration guide → announcement.
