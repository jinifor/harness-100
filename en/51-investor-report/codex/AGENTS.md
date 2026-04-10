# Investor Report Harness

This folder is the Codex version of the Investor Report Harness. Start with the local `investor-report` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/investor-report/SKILL.md`
- Specialist agents: `.codex/agents/financial-analyst.toml`, `.codex/agents/ir-reviewer.toml`, `.codex/agents/kpi-designer.toml`, `.codex/agents/market-analyst.toml`, `.codex/agents/strategy-updater.toml`
- Extension skills: `.agents/skills/financial-ratio-analyzer/SKILL.md`, `.agents/skills/ir-narrative-builder/SKILL.md`, `.agents/skills/kpi-benchmark-engine/SKILL.md`

## Workflow

- Start full-pipeline work with `investor-report`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Investor report generation: an agent team collaborates to produce financial performance analysis, KPI dashboard, market trends, strategy updates, and risk disclosures.

## Deliverables

- `00_input.md` — Organized user input
- `01_financial_analysis.md` — Financial performance analysis report
- `02_kpi_dashboard.md` — KPI dashboard
- `03_market_trends.md` — Market trends report
- `04_strategy_update.md` — Strategy update and risk disclosure
- `05_review_report.md` — Review report
- `06_investor_report_final.md` — Final integrated report
