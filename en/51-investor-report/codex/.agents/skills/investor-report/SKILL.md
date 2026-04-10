---
name: investor-report
description: >-
  Trigger when: the user wants the `investor-report` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Investor Report Harness

Investor report generation: an agent team collaborates to produce financial performance analysis, KPI dashboard, market trends, strategy updates, and risk disclosures.

## Specialist Agents

- `financial-analyst`: Financial analysis expert. Analyzes P&L, cash flow, and key financial metrics, interprets period-over-period and budget-vs-actual variances, and writes the financial section from an investor perspective.
- `ir-reviewer`: IR report reviewer (QA). Cross-validates consistency across financial, KPI, market, and strategy sections, and evaluates the report's persuasiveness, transparency, and completeness from an investor perspective.
- `kpi-designer`: KPI dashboard design expert. Selects key performance indicators from an investor perspective and systematizes trend visualization, benchmark comparisons, and goal achievement rates.
- `market-analyst`: Market trends analysis expert. Analyzes industry trends, competitive landscape changes, regulatory developments, and macroeconomic impacts to write the market section of the investor report.
- `strategy-updater`: Strategy update writer. Writes the progress of business strategy, future roadmap, and risk disclosures from an investor perspective. Also completes the final integrated report.

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
- `01_financial_analysis.md` — Financial performance analysis report
- `02_kpi_dashboard.md` — KPI dashboard
- `03_market_trends.md` — Market trends report
- `04_strategy_update.md` — Strategy update and risk disclosure
- `05_review_report.md` — Review report
- `06_investor_report_final.md` — Final integrated report

## Extension Skills

- `.agents/skills/financial-ratio-analyzer/SKILL.md`
- `.agents/skills/ir-narrative-builder/SKILL.md`
- `.agents/skills/kpi-benchmark-engine/SKILL.md`
