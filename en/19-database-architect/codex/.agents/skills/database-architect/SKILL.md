---
name: database-architect
description: >-
  Trigger when: the user wants the `database-architect` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Database Architect Harness

A harness where an agent team collaborates to perform DB design from modeling through migration, indexing, and query optimization.

## Specialist Agents

- `data-modeler`: Data Modeler. Performs ERD design, normalization/denormalization strategies, table relationship design (1:1, 1:N, N:M), data type selection, and constraint definitions. Proficient in both RDBMS (PostgreSQL, MySQL) and NoSQL (MongoDB, DynamoDB).
- `integration-reviewer`: Integration Reviewer (QA). Cross-validates alignment across data model, migration, performance, and security artifacts, and evaluates operational readiness.
- `migration-manager`: Migration Manager. Generates DDL scripts, manages migration versioning, designs rollback strategies, creates seed data, and designs zero-downtime migration procedures.
- `performance-analyst`: DB Performance Analyst. Designs index strategies, query optimization, execution plan (EXPLAIN) analysis, partitioning, connection pooling, and caching strategies.
- `security-auditor`: DB Security Auditor. Verifies and designs access control (RBAC), data encryption (TDE, column-level encryption), SQL injection defense, audit logging, and backup/recovery strategies.

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
- `01_data_model.md` — Data model design document
- `02_migration.sql` — Migration SQL scripts
- `02_migration_plan.md` — Migration plan
- `03_performance.md` — Performance optimization report
- `04_security.md` — Security verification report
- `05_review_report.md` — Integration review report

## Extension Skills

- `.agents/skills/normalization-patterns/SKILL.md`
- `.agents/skills/query-optimization-catalog/SKILL.md`
