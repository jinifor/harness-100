# Web Scraper Harness

This folder is the Codex version of the Web Scraper Harness. Start with the local `web-scraper` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/web-scraper/SKILL.md`
- Specialist agents: `.codex/agents/crawler-developer.toml`, `.codex/agents/data-manager.toml`, `.codex/agents/monitor-operator.toml`, `.codex/agents/parser-engineer.toml`, `.codex/agents/target-analyst.toml`
- Extension skills: `.agents/skills/anti-bot-analyzer/SKILL.md`, `.agents/skills/selector-generator/SKILL.md`

## Workflow

- Start full-pipeline work with `web-scraper`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Web scraping system construction: a harness in which an agent team collaborates to build target analysis, crawler design, parsing, storage, and monitoring.

## Deliverables

- `00_input.md` — User input summary
- `01_target_analysis.md` — Target site analysis report
- `02_crawler_design.md` — Crawler design and code
- `03_parser_logic.md` — Parsing logic and code
- `04_data_storage.md` — Data storage design
- `05_monitor_config.md` — Monitoring configuration
- `src/` — Actual scraping source code
