# Fullstack Web App Harness

This folder is the Codex version of the Fullstack Web App Harness. Start with the local `fullstack-webapp` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/fullstack-webapp/SKILL.md`
- Specialist agents: `.codex/agents/architect.toml`, `.codex/agents/backend-dev.toml`, `.codex/agents/devops-engineer.toml`, `.codex/agents/frontend-dev.toml`, `.codex/agents/qa-engineer.toml`
- Extension skills: `.agents/skills/api-security-checklist/SKILL.md`, `.agents/skills/component-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `fullstack-webapp`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to develop fullstack web apps through the pipeline of requirements, design, frontend, backend, testing, and deployment.

## Deliverables

- `_workspace/00_input.md` — Organized user input
- `_workspace/01_architecture.md` — Architecture design document
- `_workspace/02_api_spec.md` — API specification
- `_workspace/03_db_schema.md` — DB schema
- `_workspace/04_test_plan.md` — Test plan
- `_workspace/05_deploy_guide.md` — Deployment guide
- `_workspace/06_review_report.md` — Review report
- `src/` — Source code (frontend + backend)
