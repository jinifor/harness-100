# Competency Modeler Harness

This folder is the Codex version of the Competency Modeler Harness. Start with the local `competency-modeler` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/competency-modeler/SKILL.md`
- Specialist agents: `.codex/agents/competency-architect.toml`, `.codex/agents/development-planner.toml`, `.codex/agents/job-analyst.toml`, `.codex/agents/rubric-designer.toml`
- Extension skills: `.agents/skills/bars-assessment/SKILL.md`, `.agents/skills/ksa-taxonomy/SKILL.md`

## Workflow

- Start full-pipeline work with `competency-modeler`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to perform the full competency modeling pipeline: job analysis → competency dictionary → assessment rubric design → development plan → competency matrix.

## Deliverables

- `00_input.md` — Organized user input
- `01_job_analysis.md` — Job analysis report
- `02_competency_dictionary.md` — Competency dictionary
- `03_assessment_rubric.md` — Assessment rubric
- `04_development_plan.md` — Competency development plan
- `05_competency_matrix.md` — Competency matrix
