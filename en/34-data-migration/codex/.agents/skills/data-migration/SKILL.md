---
name: data-migration
description: >-
  Trigger when: the user wants the `data-migration` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Data Migration Harness

Data migration: a harness in which an agent team collaborates to perform source analysis, schema mapping, transformation script generation, validation queries, and rollback planning.

## Specialist Agents

- `rollback-planner`: Rollback and emergency response specialist. Develops backup strategies, rollback scripts, emergency procedures, decision trees, and communication plans.
- `schema-mapper`: Schema mapping specialist. Systematically designs field mappings, type conversion rules, business transformation logic, and default value definitions between source and target systems.
- `script-developer`: Migration script developer. Generates executable scripts including ETL transformation code, incremental migration logic, batch processing, and performance optimization.
- `source-analyst`: Source system analysis specialist. Performs schema reverse-engineering, data profiling, inter-table dependency mapping, and data quality diagnostics on the source database.
- `validation-engineer`: Migration validation engineer. Designs and executes data integrity validation queries, row count matching, business rule validation, and regression test suites.

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

- `00_input.md` — User input and migration requirements
- `01_source_analysis.md` — Source system analysis report
- `02_schema_mapping.md` — Schema mapping specification
- `03_migration_scripts/` — Transformation scripts directory
- `04_validation_suite.md` — Validation queries and test suite
- `05_rollback_plan.md` — Rollback and emergency response plan

## Extension Skills

- `.agents/skills/data-validation-patterns/SKILL.md`
- `.agents/skills/type-mapping-encyclopedia/SKILL.md`
