# Design System Harness

This folder is the Codex version of the Design System Harness. Start with the local `design-system` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/design-system/SKILL.md`
- Specialist agents: `.codex/agents/a11y-auditor.toml`, `.codex/agents/component-developer.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/storybook-builder.toml`, `.codex/agents/token-designer.toml`
- Extension skills: `.agents/skills/token-generator/SKILL.md`, `.agents/skills/wcag-checker/SKILL.md`

## Workflow

- Start full-pipeline work with `design-system`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- UI design system construction: a harness in which an agent team collaborates to create design tokens, a component library, Storybook, accessibility verification, and documentation.

## Deliverables

- `00_input.md` — User input and brand information
- `01_design_tokens/` — Design token definition files
- `02_components/` — Component library code
- `03_storybook/` — Storybook stories and configuration
- `04_a11y_report.md` — Accessibility verification report
- `05_docs/` — Design system documentation
