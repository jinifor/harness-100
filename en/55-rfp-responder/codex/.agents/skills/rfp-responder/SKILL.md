---
name: rfp-responder
description: >-
  Trigger when: the user wants the `rfp-responder` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# RFP Responder Harness

A harness where an agent team collaborates to create RFI/RFP responses: requirements analysis, capability matching, technical proposal, pricing proposal, and differentiation strategy.

## Specialist Agents

- `capability-matcher`: Capability matching expert. Maps company performance records, personnel, and technical capabilities to RFP requirements based on requirements analysis, and derives gaps and remediation strategies.
- `pricing-strategist`: Pricing strategy expert. Creates optimal price proposals considering cost estimation, pricing strategy, and competitive positioning.
- `proposal-reviewer`: Proposal reviewer (QA). Cross-validates consistency across requirements analysis, capability matching, technical proposal, and pricing proposal, and checks differentiation strategy consistency and final completeness.
- `requirement-analyst`: RFP requirements analysis expert. Precisely dissects RFP/RFI documents to classify mandatory/optional requirements, and identifies per-criterion scoring and hidden needs.
- `technical-proposer`: Technical proposal writing expert. Based on requirements analysis and capability matching, writes technical proposals including methodology, architecture, implementation schedule, and quality management plans.

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
- `01_requirement_analysis.md` — Requirements analysis
- `02_capability_matching.md` — Capability matching table
- `03_technical_proposal.md` — Technical proposal
- `04_pricing_proposal.md` — Pricing proposal
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/pricing-calculator/SKILL.md`
- `.agents/skills/win-theme-builder/SKILL.md`
