---
name: gov-funding-plan
description: >-
  Trigger when: the user wants the `gov-funding-plan` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Government Funding Plan Harness

Government funding proposal: a harness where an agent team collaborates to perform announcement analysis → business plan writing → technical writing → budget planning → submission review.

## Specialist Agents

- `announcement-analyst`: Announcement analyst. Systematically analyzes government funding program announcements including eligibility requirements, evaluation criteria, scoring weights, preferential considerations, and required documents.
- `biz-writer`: Business feasibility writer. Writes market analysis, commercialization strategy, marketing plan, expected outcomes, and utilization plan according to government business plan formats.
- `budget-planner`: Budget planner. Performs government R&D budget allocation by cost category, personnel cost calculation, indirect cost estimation, private co-funding allocation, and documentation guidance.
- `submission-reviewer`: Submission reviewer (QA). Cross-validates consistency between announcement requirements, technical section, business section, and budget. Identifies missing items, deduction factors, and assesses submission readiness.
- `tech-writer`: Technical section writer. Writes the technology development objectives, development content, technical differentiation, research methodology, and implementation framework according to government business plan formats.

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

- `.agents/skills/budget-standard-checker/SKILL.md`
- `.agents/skills/scoring-optimizer/SKILL.md`
