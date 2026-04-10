---
name: changelog-generator
description: >-
  Trigger when: the user wants the `changelog-generator` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Changelog Generator Harness

Changelog generation: a harness where an agent team collaborates to perform commit analysis → change classification → release note writing → migration guide → announcement.

## Specialist Agents

- `announcement-writer`: Announcement writer. Crafts release information into formats suitable for various channels including blog posts, social media posts, and email newsletters.
- `change-classifier`: Change classifier. Groups all changes into semantic units based on commit analysis results and classifies them by user impact level.
- `commit-analyst`: Commit analyst. Analyzes git history to extract all changes between two versions. Examines commit messages, PRs, branch strategies, and contributor information.
- `migration-guide-writer`: Migration guide writer. Creates detailed upgrade guides for Breaking Changes. Provides code transformation examples, step-by-step procedures, and compatibility matrices.
- `release-note-writer`: Release note writer. Creates user-friendly release notes based on change classification results. Supports CHANGELOG.md and GitHub Release formats.

## Workflow

1. Gather the request, constraints, and any existing source material.
2. Save the starting context in `_workspace/00_input.md` when that helps downstream handoff.
3. Run the specialists needed for the request scope, using numbered `_workspace/` artifacts as handoff points.
4. Run the reviewer or synthesizer role, if present, after prerequisite artifacts exist.
5. Report skipped phases, limitations, and reused inputs in the final result.

## Output Rules

- Keep the source `.claude` files untouched.
- Keep all harness deliverables in `_workspace/`.
- If existing files already satisfy a phase, reference or copy them into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Extension Skills

- `.agents/skills/commit-parser/SKILL.md`
- `.agents/skills/semver-analyzer/SKILL.md`
