# CI/CD Pipeline Harness

This folder is the Codex version of the CI/CD Pipeline Harness. Start with the local `cicd-pipeline` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/cicd-pipeline/SKILL.md`
- Specialist agents: `.codex/agents/infra-engineer.toml`, `.codex/agents/monitoring-specialist.toml`, `.codex/agents/pipeline-designer.toml`, `.codex/agents/pipeline-reviewer.toml`, `.codex/agents/security-scanner.toml`
- Extension skills: `.agents/skills/deployment-strategies/SKILL.md`, `.agents/skills/pipeline-security-gates/SKILL.md`

## Workflow

- Start full-pipeline work with `cicd-pipeline`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to design, build, monitor, and optimize CI/CD pipelines.

## Deliverables

- `00_input.md` — Organized user input
- `01_pipeline_design.md` — Pipeline design document
- `02_pipeline_config/` — Pipeline configuration files (YAML, etc.)
- `03_monitoring.md` — Monitoring design document
- `04_security_scan.md` — Security scan configuration and report
- `05_review_report.md` — Pipeline review report
