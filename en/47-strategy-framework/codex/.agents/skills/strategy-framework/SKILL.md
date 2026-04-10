---
name: strategy-framework
description: >-
  Trigger when: the user wants the `strategy-framework` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Strategy Framework Harness

A harness where an agent team collaborates to generate an organizational strategy framework in sequence: OKR Design, BSC Mapping, SWOT Analysis, Vision & Mission Statement, and Strategy Execution Roadmap.

## Specialist Agents

- `bsc-analyst`: BSC (Balanced Scorecard) Analyst. Maps the OKR system across the four perspectives — Financial, Customer, Internal Process, and Learning & Growth — and designs the causal relationships and strategy map.
- `okr-designer`: OKR design expert. Structures the organization's strategic direction into Objectives and Key Results, and designs alignment (cascading) between upper and lower-level OKRs.
- `strategy-reviewer`: Strategy Framework Reviewer (QA). Cross-validates logical consistency across OKR, BSC, SWOT, vision/mission, and roadmap, and identifies strategic contradictions, gaps, and quality issues.
- `strategy-writer`: Strategy Document Writer. Synthesizes OKR, BSC, and SWOT results to produce the vision & mission statement and strategy execution roadmap. Finalizes strategy documents for executive reporting.
- `swot-specialist`: SWOT analysis expert. Systematically analyzes the organization's internal strengths/weaknesses and external opportunities/threats, and derives actionable strategies through the TOWS matrix.

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
- `01_okr_design.md` — OKR design document
- `02_bsc_mapping.md` — BSC mapping table
- `03_swot_analysis.md` — SWOT analysis report
- `04_vision_mission.md` — Vision & mission statement
- `05_strategy_roadmap.md` — Strategy execution roadmap
- `06_review_report.md` — Review report

## Extension Skills

- `.agents/skills/okr-quality-checker/SKILL.md`
- `.agents/skills/tows-matrix-builder/SKILL.md`
