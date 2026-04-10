---
name: brand-identity
description: >-
  Trigger when: the user wants the `brand-identity` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Brand Identity Harness

A harness where an agent team collaborates to design brand identity from naming through slogans, tone and manner, and visual guidelines.

## Specialist Agents

- `brand-strategist`: Brand strategist. Conducts market analysis, competitive positioning, target persona development, brand archetype selection, and differentiation strategy.
- `copywriter`: Brand copywriter. Creates slogans, taglines, brand stories, and tone-and-manner guides.
- `identity-reviewer`: Brand identity reviewer (QA). Cross-validates consistency across strategy, naming, verbal identity, and visual identity, and identifies brand coherence issues.
- `naming-specialist`: Brand naming specialist. Develops naming candidates based on brand strategy and reviews domain availability, trademark conflicts, and pronunciation ease.
- `visual-director`: Visual director. Designs the brand color system, typography, logo concepts, and visual guidelines.

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
- `01_brand_strategy.md` — Brand strategy report
- `02_naming_candidates.md` — Naming candidates
- `03_verbal_identity.md` — Verbal identity (slogans, tone and manner)
- `04_visual_identity.md` — Visual identity (color, typography, logo)
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/brand-archetype/SKILL.md`
- `.agents/skills/color-psychology/SKILL.md`
- `.agents/skills/naming-methodology/SKILL.md`
