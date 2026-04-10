---
name: book-publishing
description: >-
  Trigger when: the user wants the `book-publishing` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Book Publishing Harness

A harness where an agent team collaborates to produce e-book publishing deliverables: manuscript editing, cover design, table of contents, metadata, and distribution setup.

## Specialist Agents

- `cover-designer`: Cover designer. Designs cover concepts matching the book's genre, tone, and target audience, and produces covers using Gemini image generation. Includes typography, color, and composition.
- `manuscript-editor`: Manuscript editor. Performs structural editing (chapter organization, flow), style correction (tone unification, readability), and content consistency verification. Includes both developmental editing and line editing.
- `metadata-manager`: Metadata manager. Handles ISBN, book classification (BISAC/KDC), book descriptions, keywords, pricing, and distribution platform settings. Manages all metadata required for e-book distribution.
- `proofreader`: Proofreader. Reviews spelling, grammar, spacing, foreign word notation, number notation, punctuation, and terminology standardization. Performs precise proofreading based on language conventions.
- `publishing-reviewer`: Publishing reviewer (QA). Cross-validates consistency across manuscript, proofreading, cover, and metadata. Performs final verification of publishing spec compliance, legal requirements, and distribution readiness.

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
- `01_edited_manuscript.md` — Edited manuscript
- `02_proofread_report.md` — Proofreading report
- `03_cover_concept.md` — Cover concept/images
- `04_metadata.md` — Metadata/distribution settings
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/book-metadata-seo/SKILL.md`
- `.agents/skills/cover-design-psychology/SKILL.md`
- `.agents/skills/developmental-editing/SKILL.md`
