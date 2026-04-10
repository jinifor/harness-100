---
name: youtube-production
description: >-
  Trigger when: the task is to produce a YouTube video package end to end: strategy, script, thumbnail concept, SEO package, subtitle file, and final review. Do not trigger when: the user only wants a hook, thumbnail advice, or isolated SEO help without the full production pipeline. Expected input: topic, prompt, existing brief, or source material. Expected output: the `_workspace/` deliverables for strategy, script, thumbnail, SEO, subtitles, and review.
---

# YouTube Production

Use this skill to coordinate the full YouTube production harness.

## Workflow

1. Gather the topic, audience, constraints, and any existing source material.
2. Produce the strategy brief with `content-strategist`.
3. Produce the spoken script with `scriptwriter`.
4. Produce the thumbnail concept with `thumbnail-designer`.
5. Produce titles, metadata, and subtitles with `seo-optimizer`.
6. Run `production-reviewer` on the completed package.

## Output Rules

- Keep all deliverables in `_workspace/`.
- Preserve the same core angle across strategy, script, thumbnail, and SEO.
- If image generation is unavailable, keep the thumbnail prompt in the concept sheet.
- If search is unavailable, continue with the best available source context and note the limitation.

## Extension Skills

- Use `hook-writing` when the script needs a sharper opening.
- Use `thumbnail-psychology` when the thumbnail needs deeper visual optimization.
