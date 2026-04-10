# Sales Enablement Harness

This folder is the Codex version of the Sales Enablement Harness. Start with the local `sales-enablement` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/sales-enablement/SKILL.md`
- Specialist agents: `.codex/agents/customer-analyst.toml`, `.codex/agents/followup-manager.toml`, `.codex/agents/presenter.toml`, `.codex/agents/proposal-writer.toml`, `.codex/agents/sales-reviewer.toml`
- Extension skills: `.agents/skills/objection-handler/SKILL.md`, `.agents/skills/roi-calculator/SKILL.md`

## Workflow

- Start full-pipeline work with `sales-enablement`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A sales enablement pipeline where an agent team collaborates to produce: Customer Analysis, Proposal, Presentation, and Follow-up Plan.

## Deliverables

- `00_input.md` — Organized user input
- `01_customer_analysis.md` — Customer analysis report
- `02_proposal.md` — Proposal
- `03_presentation.md` — Presentation outline
- `04_followup_plan.md` — Follow-up plan
- `05_review_report.md` — Review report
