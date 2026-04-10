---
name: sales-enablement
description: >-
  Trigger when: the user wants the `sales-enablement` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Sales Enablement Harness

A sales enablement pipeline where an agent team collaborates to produce: Customer Analysis, Proposal, Presentation, and Follow-up Plan.

## Specialist Agents

- `customer-analyst`: Customer Analysis Expert. Analyzes the target customer's business situation, needs, decision-making structure, budget, and competitive solution usage to provide the foundation for a tailored sales strategy.
- `followup-manager`: Sales Follow-up Management Expert. Develops post-proposal follow-up schedules, email templates, objection handling scripts, and action plans through to contract closure.
- `presenter`: Sales Presentation Design Expert. Converts proposal content into a persuasive presentation storyline and slide structure. Designs tailored messaging for each DMU role.
- `proposal-writer`: Sales Proposal Writing Expert. Creates customized solution proposals based on customer analysis results, including value proposition, solution matching, ROI calculation, and pricing.
- `sales-reviewer`: Sales Enablement Reviewer (QA). Cross-validates consistency across customer analysis, proposal, presentation, and follow-up, and evaluates the persuasiveness, coherence, and completeness of the sales strategy.

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
- `01_customer_analysis.md` — Customer analysis report
- `02_proposal.md` — Proposal
- `03_presentation.md` — Presentation outline
- `04_followup_plan.md` — Follow-up plan
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/objection-handler/SKILL.md`
- `.agents/skills/roi-calculator/SKILL.md`
