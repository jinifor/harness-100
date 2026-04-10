# Content Repurposer Harness

This folder is the Codex version of the content repurposing harness. Use the local `content-repurposer` skill for the full pipeline and the specialist skills for platform adaptation and content atomization.

## Workflow

- Use `source-analyst` to analyze the original content and define the conversion strategy.
- Use `blog-writer` to produce the SEO blog post.
- Use `sns-copywriter` to produce the social media package.
- Use `presentation-builder` to produce the slide deck.
- Use `quality-reviewer` to verify message consistency and factual accuracy.

## Deliverables

- `_workspace/01_source_analysis.md`
- `_workspace/02_blog_post.md`
- `_workspace/03_sns_package.md`
- `_workspace/04_presentation.md`
- `_workspace/05_review_report.md`

## Rules

- Keep the source `.claude` files untouched.
- Preserve the source's core message while adapting the format.
- If source material is already provided, copy it into `_workspace/` and skip the matching phase.
- If the source is a URL and cannot be fetched, continue with the provided text or cached material and note the limitation.
