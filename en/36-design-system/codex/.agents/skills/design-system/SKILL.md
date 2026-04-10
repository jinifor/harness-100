---
name: design-system
description: >-
  Trigger when: the user wants the `design-system` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Design System Harness

UI design system construction: a harness in which an agent team collaborates to create design tokens, a component library, Storybook, accessibility verification, and documentation.

## Specialist Agents

- `a11y-auditor`: Accessibility (A11y) verification specialist. Verifies WCAG 2.1 AA/AAA compliance and systematically audits ARIA patterns, keyboard navigation, screen reader compatibility, and color contrast.
- `component-developer`: UI component development specialist. Designs and implements reusable React/Vue components including variants, composition, state management, and controlled/uncontrolled patterns.
- `doc-writer`: Design system documentation specialist. Writes design principles, component usage guides, design-development handoff guides, contribution guides, and versioning policies.
- `storybook-builder`: Storybook builder. Creates stories, interaction tests, and documentation pages for each component, and implements design token visualization and theme switching in Storybook.
- `token-designer`: Design token specialist. Systematically designs the foundational tokens of the design system: colors, typography, spacing, shadows, motion, and responsive breakpoints.

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

- `00_input.md` — User input and brand information
- `01_design_tokens/` — Design token definition files
- `02_components/` — Component library code
- `03_storybook/` — Storybook stories and configuration
- `04_a11y_report.md` — Accessibility verification report
- `05_docs/` — Design system documentation

## Extension Skills

- `.agents/skills/token-generator/SKILL.md`
- `.agents/skills/wcag-checker/SKILL.md`
