---
name: procurement-docs
description: >-
  Trigger when: the user wants the `procurement-docs` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Procurement Docs Harness

A procurement document set generation harness. An agent team collaborates to produce everything from requirements definition through vendor comparison, evaluation criteria, contract review, and acceptance criteria.

## Specialist Agents

- `acceptance-builder`: Acceptance criteria creation expert. Designs inspection items, test procedures, and pass/fail criteria for deliverables to enable objective acceptance testing.
- `contract-reviewer`: Contract terms review expert. Analyzes procurement contract clauses, risk provisions, SLAs, intellectual property, and termination conditions, and identifies negotiation points.
- `evaluation-designer`: Evaluation criteria design expert. Designs evaluation criteria, scoring scales, and weighting for vendor/product selection, and establishes qualitative/quantitative assessment methodologies and consensus decision processes.
- `requirements-definer`: Procurement requirements definition expert. Systematically defines technical specifications, quantities, delivery dates, budgets, and required/optional requirements to produce the foundational document for vendor selection.
- `vendor-comparator`: Vendor comparison analysis expert. Researches vendor/product candidates matching procurement requirements and creates multi-dimensional comparison tables covering features, pricing, track record, and support.

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

## Extension Skills

- `.agents/skills/contract-checklist/SKILL.md`
- `.agents/skills/vendor-scoring/SKILL.md`
