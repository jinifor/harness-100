# Podcast Studio Harness

This folder is the Codex version of the podcast production harness. Use the local `podcast-studio` skill for the full pipeline and the extension skills for interview design, audio storytelling, and growth strategy.

## Workflow

- Use `researcher` for topic, guest, and competitive episode research.
- Use `scriptwriter` for the episode script and question flow.
- Use `shownote-editor` for timestamps, summaries, links, quotes, and guest bio.
- Use `distribution-manager` for metadata, promotional copy, and release planning.
- Use `production-reviewer` to verify consistency and publish readiness.

## Deliverables

- `_workspace/01_research_brief.md`
- `_workspace/02_script.md`
- `_workspace/03_shownotes.md`
- `_workspace/04_distribution_package.md`
- `_workspace/05_review_report.md`

## Rules

- Keep the source `.claude` files untouched.
- Preserve the same core message across research, script, show notes, and distribution.
- If a source file is already provided, copy it into `_workspace/` and skip that phase.
- If web search is unavailable, continue with the best available context and note the limitation.
