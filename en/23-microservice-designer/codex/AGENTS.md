# Microservice Designer Harness

This folder is the Codex version of the Microservice Designer Harness. Start with the local `microservice-designer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/microservice-designer/SKILL.md`
- Specialist agents: `.codex/agents/architecture-reviewer.toml`, `.codex/agents/communication-designer.toml`, `.codex/agents/domain-analyst.toml`, `.codex/agents/observability-engineer.toml`, `.codex/agents/service-architect.toml`
- Extension skills: `.agents/skills/ddd-context-mapping/SKILL.md`, `.agents/skills/distributed-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `microservice-designer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for designing, decomposing, communicating, and monitoring microservice architectures. Automates the full pipeline from domain analysis to observability design.

## Deliverables

- `00_input.md` — Organized user input
- `01_domain_analysis.md` — Domain analysis report
- `02_service_design.md` — Service design document
- `03_communication_design.md` — Communication design document
- `04_observability_design.md` — Observability design document
- `05_review_report.md` — Final review report
