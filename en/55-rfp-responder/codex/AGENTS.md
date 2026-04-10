# RFP Responder Harness

This folder is the Codex version of the RFP Responder Harness. Start with the local `rfp-responder` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/rfp-responder/SKILL.md`
- Specialist agents: `.codex/agents/capability-matcher.toml`, `.codex/agents/pricing-strategist.toml`, `.codex/agents/proposal-reviewer.toml`, `.codex/agents/requirement-analyst.toml`, `.codex/agents/technical-proposer.toml`
- Extension skills: `.agents/skills/pricing-calculator/SKILL.md`, `.agents/skills/win-theme-builder/SKILL.md`

## Workflow

- Start full-pipeline work with `rfp-responder`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to create RFI/RFP responses: requirements analysis, capability matching, technical proposal, pricing proposal, and differentiation strategy.

## Deliverables

- `00_input.md` — Organized user input
- `01_requirement_analysis.md` — Requirements analysis
- `02_capability_matching.md` — Capability matching table
- `03_technical_proposal.md` — Technical proposal
- `04_pricing_proposal.md` — Pricing proposal
- `05_review_report.md` — Review report
