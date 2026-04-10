# Grant Writer Harness

This folder is the Codex version of the Grant Writer Harness. Start with the local `grant-writer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/grant-writer/SKILL.md`
- Specialist agents: `.codex/agents/announcement-analyst.toml`, `.codex/agents/budget-designer.toml`, `.codex/agents/compliance-checker.toml`, `.codex/agents/plan-writer.toml`, `.codex/agents/submission-verifier.toml`
- Extension skills: `.agents/skills/budget-rule-engine/SKILL.md`, `.agents/skills/scoring-optimizer/SKILL.md`

## Workflow

- Start full-pipeline work with `grant-writer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates on grant and funding applications: announcement analysis, business plan writing, budget design, and submission verification.

## Deliverables

- `00_input.md` — Organized user input
- `01_announcement_analysis.md` — Announcement analysis
- `02_business_plan.md` — Business plan
- `03_budget.md` — Budget plan
- `04_compliance_review.md` — Compliance review
- `05_submission_checklist.md` — Submission checklist
- `06_review_report.md` — Review report
