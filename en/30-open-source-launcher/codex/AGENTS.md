# Open Source Launcher Harness

This folder is the Codex version of the Open Source Launcher Harness. Start with the local `open-source-launcher` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/open-source-launcher/SKILL.md`
- Specialist agents: `.codex/agents/code-organizer.toml`, `.codex/agents/community-manager.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/launch-reviewer.toml`, `.codex/agents/license-specialist.toml`
- Extension skills: `.agents/skills/community-health-metrics/SKILL.md`, `.agents/skills/license-compatibility-matrix/SKILL.md`

## Workflow

- Start full-pipeline work with `open-source-launcher`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for preparing open source project launches covering code cleanup, documentation, licensing, and community building.

## Deliverables

- `00_input.md` — Organized user input
- `01_code_organization.md` — Code cleanup plan and results
- `02_documentation.md` — Documentation package (README, guides, etc.)
- `03_license_review.md` — License review and selection
- `04_community_setup.md` — Community setup and governance
- `05_launch_report.md` — Launch review report
- `generated_files/` — Generated files (README, LICENSE, CONTRIBUTING, etc.)
