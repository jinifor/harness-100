# Book Publishing Harness

This folder is the Codex version of the Book Publishing Harness. Start with the local `book-publishing` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/book-publishing/SKILL.md`
- Specialist agents: `.codex/agents/cover-designer.toml`, `.codex/agents/manuscript-editor.toml`, `.codex/agents/metadata-manager.toml`, `.codex/agents/proofreader.toml`, `.codex/agents/publishing-reviewer.toml`
- Extension skills: `.agents/skills/book-metadata-seo/SKILL.md`, `.agents/skills/cover-design-psychology/SKILL.md`, `.agents/skills/developmental-editing/SKILL.md`

## Workflow

- Start full-pipeline work with `book-publishing`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to produce e-book publishing deliverables: manuscript editing, cover design, table of contents, metadata, and distribution setup.

## Deliverables

- `00_input.md` — Organized user input
- `01_edited_manuscript.md` — Edited manuscript
- `02_proofread_report.md` — Proofreading report
- `03_cover_concept.md` — Cover concept/images
- `04_metadata.md` — Metadata/distribution settings
- `05_review_report.md` — Review report
