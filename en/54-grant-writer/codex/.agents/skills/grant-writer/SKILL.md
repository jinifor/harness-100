---
name: grant-writer
description: >-
  Trigger when: the user wants the `grant-writer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Grant Writer Harness

A harness where an agent team collaborates on grant and funding applications: announcement analysis, business plan writing, budget design, and submission verification.

## Specialist Agents

- `announcement-analyst`: Grant/funding announcement analysis expert. Analyzes eligibility requirements, evaluation criteria, scoring systems, and key keywords from announcements to provide the foundation for application strategy.
- `budget-designer`: Budget design expert. Calculates per-category budgets compliant with announcement regulations, and creates matching fund plans, execution plans, and settlement guides.
- `compliance-checker`: Compliance verification expert. Verifies that the business plan and budget fully comply with announcement requirements, and derives improvements for score optimization.
- `plan-writer`: Business plan writing expert. Writes business plans optimized for evaluation criteria based on announcement analysis results. Systematically describes technical merit, business viability, and execution capability.
- `submission-verifier`: Submission verification expert (QA). Performs final verification of the application package completeness and creates submission checklists and submission guides.

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
- `01_announcement_analysis.md` — Announcement analysis
- `02_business_plan.md` — Business plan
- `03_budget.md` — Budget plan
- `04_compliance_review.md` — Compliance review
- `05_submission_checklist.md` — Submission checklist
- `06_review_report.md` — Review report

## Extension Skills

- `.agents/skills/budget-rule-engine/SKILL.md`
- `.agents/skills/scoring-optimizer/SKILL.md`
