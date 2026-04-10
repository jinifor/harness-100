---
name: content-repurposer
description: >-
  Trigger when: the task is to convert one source into multiple formats such as blog, social media, presentation, or newsletter-style outputs. Do not trigger when: the user only wants a single-format rewrite or isolated formatting advice. Expected input: source text, URL, file, or content brief. Expected output: the `_workspace/` deliverables for analysis, blog, social, presentation, and review.
---

# Content Repurposer

Use this skill to coordinate the full content repurposing harness.

## Workflow

1. Gather the source, target formats, and any constraints.
2. Produce the source analysis with `source-analyst`.
3. Produce the blog conversion with `blog-writer`.
4. Produce the social package with `sns-copywriter`.
5. Produce the presentation with `presentation-builder`.
6. Run `quality-reviewer` on the completed package.

## Output Rules

- Keep all deliverables in `_workspace/`.
- Preserve the source's core message across all formats.
- If source material is provided, copy it into `_workspace/` and skip the matching phase.
- If the source is a URL and cannot be fetched, continue with the available text and note the limitation.

## Extension Skills

- Use `platform-adaptation` for platform-native conversion rules.
- Use `content-atomization` for breaking the source into reusable units.
