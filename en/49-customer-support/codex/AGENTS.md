# Customer Support Harness

This folder is the Codex version of the Customer Support Harness. Start with the local `customer-support` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/customer-support/SKILL.md`
- Specialist agents: `.codex/agents/cs-analyst.toml`, `.codex/agents/cs-reviewer.toml`, `.codex/agents/escalation-manager.toml`, `.codex/agents/faq-builder.toml`, `.codex/agents/response-specialist.toml`
- Extension skills: `.agents/skills/csat-analyzer/SKILL.md`, `.agents/skills/escalation-flowchart/SKILL.md`

## Workflow

- Start full-pipeline work with `customer-support`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Build a customer support system: an agent team collaborates to produce FAQ, response manuals, escalation policies, and analytics.

## Deliverables

- `00_input.md` — Organized user input
- `01_faq.md` — FAQ document
- `02_response_manual.md` — Response manual
- `03_escalation_policy.md` — Escalation policy
- `04_cs_analytics.md` — CS analytics framework
- `05_review_report.md` — Review report
