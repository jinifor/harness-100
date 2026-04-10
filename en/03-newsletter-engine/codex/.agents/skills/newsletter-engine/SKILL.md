---
name: newsletter-engine
description: >-
  Trigger when: the task is to produce a newsletter end to end: curation, writing, A/B testing, final editing, and review. Do not trigger when: the user only wants email copy tips, segmentation strategy, or deliverability help without the full pipeline. Expected input: topic, audience, brand tone, or existing content. Expected output: the `_workspace/` deliverables for curation, draft, test plan, final edit, and review.
---

# Newsletter Engine

Use this skill to coordinate the full newsletter harness.

## Workflow

1. Gather topic, audience, constraints, and existing material.
2. Produce the curation brief with `curator`.
3. Produce the newsletter draft with `copywriter`.
4. Produce the A/B test plan with `analyst`.
5. Produce the final version with `editor-in-chief`.
6. Run `quality-reviewer` on the completed issue.

## Output Rules

- Keep all deliverables in `_workspace/`.
- Preserve the same core message from curation through final edit.
- If existing content is provided, copy it into `_workspace/` and skip the matching phase.
- If web search is unavailable, continue with the best available context and note the limitation.

## Extension Skills

- Use `email-copywriting` for subject lines, preheaders, and F-pattern body structure.
- Use `audience-segmentation` for subscriber segmentation and send timing.
- Use `deliverability-optimization` for spam avoidance, authentication, and legal checks.
