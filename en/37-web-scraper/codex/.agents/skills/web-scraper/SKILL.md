---
name: web-scraper
description: >-
  Trigger when: the user wants the `web-scraper` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Web Scraper Harness

Web scraping system construction: a harness in which an agent team collaborates to build target analysis, crawler design, parsing, storage, and monitoring.

## Specialist Agents

- `crawler-developer`: Web crawler developer. Designs and implements efficient, reliable crawlers based on target analysis results. Handles request strategies, session management, retry logic, and proxy rotation.
- `data-manager`: Data manager. Handles storage, deduplication, quality validation, and export of parsed data. Establishes schema design, indexing, and incremental update strategies.
- `monitor-operator`: Monitoring operator. Handles health checks, site change detection, logging, alerting, and scheduling for the scraping system. Ensures stable system operation.
- `parser-engineer`: Parsing engineer. Designs and implements parsing logic to accurately extract target data from crawled raw data. Handles CSS selectors, XPath, regex, and JSON parsing.
- `target-analyst`: Web scraping target analyst. Performs target site structure analysis, robots.txt/ToS review, tech stack analysis, anti-bot mechanism identification, and legal risk assessment.

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

- `00_input.md` — User input summary
- `01_target_analysis.md` — Target site analysis report
- `02_crawler_design.md` — Crawler design and code
- `03_parser_logic.md` — Parsing logic and code
- `04_data_storage.md` — Data storage design
- `05_monitor_config.md` — Monitoring configuration
- `src/` — Actual scraping source code

## Extension Skills

- `.agents/skills/anti-bot-analyzer/SKILL.md`
- `.agents/skills/selector-generator/SKILL.md`
