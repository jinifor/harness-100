# Newsletter Engine Harness

This folder is the Codex version of the newsletter harness. Use the local `newsletter-engine` skill for the full pipeline and the specialist skills for email copy, segmentation, and deliverability.

## Workflow

- Use `curator` to collect sources, analyze trends, and choose the issue theme.
- Use `copywriter` to draft the newsletter body and subject lines.
- Use `analyst` to design A/B tests, send timing, and forecasts.
- Use `editor-in-chief` to finalize tone, flow, and compliance.
- Use `quality-reviewer` to verify the complete issue.

## Deliverables

- `_workspace/01_curation_brief.md`
- `_workspace/02_newsletter_draft.md`
- `_workspace/03_ab_test_plan.md`
- `_workspace/04_editorial_final.md`
- `_workspace/05_review_report.md`

## Rules

- Keep the source `.claude` files untouched.
- Preserve the same core message from curation through final edit.
- If existing newsletter content is provided, copy it into `_workspace/` and skip the matching phase.
- If web search is unavailable, continue with the best available context and note the limitation.
