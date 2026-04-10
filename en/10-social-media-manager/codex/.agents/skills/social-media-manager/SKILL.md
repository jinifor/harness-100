---
name: social-media-manager
description: >-
  Trigger when: the user wants the `social-media-manager` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Social Media Manager Harness

A harness where an agent team collaborates to produce SNS content calendars, post copy, hashtags, and performance analysis.

## Specialist Agents

- `copywriter`: SNS copywriter. Writes post copy, captions, and CTAs tailored to each platform. Optimizes for each platform's grammar — Instagram captions, Twitter threads, TikTok scripts, LinkedIn posts.
- `hashtag-analyst`: Hashtag analyst. Designs optimal hashtag sets per post, analyzes trend hashtags, researches competitor hashtags, and develops brand hashtag strategy.
- `performance-reviewer`: SNS performance reviewer (QA). Cross-validates consistency across strategy, posts, visuals, and hashtags. Verifies KPI alignment, platform suitability, and brand consistency, providing feedback.
- `sns-strategist`: SNS strategist. Performs channel-specific analysis, target audience definition, content calendar design, and campaign structure planning. Establishes optimized strategies for each platform (Instagram, Twitter/X, TikTok, Facebook, LinkedIn).
- `visual-planner`: SNS visual planner. Designs image concepts per post, card news layouts, Reels/short-form storyboards, and visual guidelines.

## Workflow

1. Gather the request, constraints, and any existing source material.
2. Save the starting context in `_workspace/00_input.md` when that helps downstream handoff.
3. Run the specialists needed for the request scope, using numbered `_workspace/` artifacts as handoff points.
4. Run the reviewer or synthesizer role, if present, after prerequisite artifacts exist.
5. Report skipped phases, limitations, and reused inputs in the final result.

## Output Rules

- Keep the source `.claude` files untouched.
- Keep all harness deliverables in `_workspace/`.
- If existing files already satisfy a phase, reference or copy them into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Deliverables

- `00_input.md` — Organized user input
- `01_strategy.md` — SNS strategy/content calendar
- `02_posts.md` — Post copy collection
- `03_visuals.md` — Visual plan
- `04_hashtags.md` — Hashtag strategy
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/hashtag-science/SKILL.md`
- `.agents/skills/platform-algorithms/SKILL.md`
- `.agents/skills/viral-copywriting/SKILL.md`
