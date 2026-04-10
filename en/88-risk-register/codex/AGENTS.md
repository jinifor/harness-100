# Risk Register Harness

This folder is the Codex version of the Risk Register Harness. Start with the local `risk-register` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/risk-register/SKILL.md`
- Specialist agents: `.codex/agents/assessment-analyst.toml`, `.codex/agents/monitoring-planner.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/response-strategist.toml`, `.codex/agents/risk-identifier.toml`
- Extension skills: `.agents/skills/risk-response-patterns/SKILL.md`, `.agents/skills/risk-scoring-matrix/SKILL.md`

## Workflow

- Start full-pipeline work with `risk-register`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- project risk managementversus: riskidentification→probability·impactassessment→responsestrategyestablish→monitoringplan→statusreportto A harness where an agent team collaborates to produce deliverables.
