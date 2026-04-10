---
name: fullstack-webapp
description: >-
  Trigger when: the user wants the `fullstack-webapp` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Fullstack Web App Harness

A harness where an agent team collaborates to develop fullstack web apps through the pipeline of requirements, design, frontend, backend, testing, and deployment.

## Specialist Agents

- `architect`: System architect. Analyzes requirements and performs system architecture, technology stack selection, DB modeling, and API design. Produces design documents that enable frontend/backend/QA/DevOps teams to begin work immediately.
- `backend-dev`: Backend developer. Implements APIs, database integration, authentication/authorization, and business logic. Translates the architecture design's API spec and DB schema into code.
- `devops-engineer`: DevOps engineer. Handles CI/CD pipeline setup, infrastructure configuration, deployment automation, and monitoring. Designs and implements the deployment path from development to production.
- `frontend-dev`: Frontend developer. Implements React/Next.js frontend based on the architecture design. Handles UI components, page routing, state management, API integration, and responsive design.
- `qa-engineer`: QA engineer. Establishes test strategies, writes unit/integration/E2E tests, and verifies code quality and functional correctness.

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

- `_workspace/00_input.md` — Organized user input
- `_workspace/01_architecture.md` — Architecture design document
- `_workspace/02_api_spec.md` — API specification
- `_workspace/03_db_schema.md` — DB schema
- `_workspace/04_test_plan.md` — Test plan
- `_workspace/05_deploy_guide.md` — Deployment guide
- `_workspace/06_review_report.md` — Review report
- `src/` — Source code (frontend + backend)

## Extension Skills

- `.agents/skills/api-security-checklist/SKILL.md`
- `.agents/skills/component-patterns/SKILL.md`
