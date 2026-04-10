# Translation & Localization Harness

This folder is the Codex version of the Translation & Localization Harness. Start with the local `translation-localization` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/translation-localization/SKILL.md`
- Specialist agents: `.codex/agents/localizer.toml`, `.codex/agents/quality-reviewer.toml`, `.codex/agents/style-harmonizer.toml`, `.codex/agents/terminology-manager.toml`, `.codex/agents/translator.toml`
- Extension skills: `.agents/skills/cultural-adaptation-guide/SKILL.md`, `.agents/skills/translation-quality-mqm/SKILL.md`

## Workflow

- Start full-pipeline work with `translation-localization`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to perform multilingual translation, localization, cultural adaptation, and terminology management.

## Deliverables

- `00_input.md` — Organized user input
- `01_source_analysis.md` — Source analysis/translation strategy
- `02_terminology.md` — Glossary
- `03_translation.md` — Translated text
- `04_localization.md` — Localization applied results
- `05_review_report.md` — Quality review report
