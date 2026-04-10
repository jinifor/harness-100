---
name: podcast-studio
description: >-
  Trigger when: the task is to produce a podcast episode end to end: research, scripting, show notes, distribution, and final QA. Do not trigger when: the user only wants interview questions, audio storytelling advice, or podcast growth tactics without the full production pipeline. Expected input: topic, guest, request, or existing source material. Expected output: the `_workspace/` deliverables for research, script, show notes, distribution, and review.
---

# Podcast Studio

Use this skill to coordinate the full podcast production harness.

## Workflow

1. Gather topic, guest, show tone, constraints, and any existing source material.
2. Produce the research brief with `researcher`.
3. Produce the episode script with `scriptwriter`.
4. Produce show notes with `shownote-editor`.
5. Produce the distribution package with `distribution-manager`.
6. Run `production-reviewer` on the completed package.

## Output Rules

- Keep all deliverables in `_workspace/`.
- Preserve the same core message across research, script, show notes, and distribution.
- If source files are provided, copy them into `_workspace/` and skip the matching phase.
- If web search is unavailable, continue with the best available context and note the limitation.

## Extension Skills

- Use `interview-techniques` for guest question design and conversation flow.
- Use `audio-storytelling` for pacing, narrative structure, and sound design.
- Use `podcast-growth` for platform metadata and promotion strategy.
