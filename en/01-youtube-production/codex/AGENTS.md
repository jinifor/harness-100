# YouTube Production Harness

This folder is the Codex version of the YouTube production harness. Use the local `youtube-production` skill for the full pipeline and the specialist skills for hook writing and thumbnail psychology.

## Workflow

- Read the topic, existing brief, or user request first.
- Use `content-strategist` to produce the strategy brief.
- Use `scriptwriter` to turn the brief into a spoken script.
- Use `thumbnail-designer` to create the thumbnail concept and prompt.
- Use `seo-optimizer` to produce titles, description, tags, chapters, and subtitles.
- Use `production-reviewer` to cross-check the full package.

## Deliverables

- `_workspace/01_strategist_brief.md`
- `_workspace/02_scriptwriter_script.md`
- `_workspace/03_thumbnail_concept.md`
- `_workspace/04_seo_package.md`
- `_workspace/subtitle.srt`
- `_workspace/05_review_report.md`

## Rules

- Keep the source `.claude` files untouched.
- Preserve the core angle across strategy, script, thumbnail, and SEO.
- If image generation is unavailable, keep the thumbnail prompt in the concept sheet.
- If web search fails, continue with user-provided context and note the limitation.
