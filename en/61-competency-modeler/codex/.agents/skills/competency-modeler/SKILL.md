---
name: competency-modeler
description: >-
  Trigger when: the user wants the `competency-modeler` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Competency Modeler Harness

A harness where an agent team collaborates to perform the full competency modeling pipeline: job analysis → competency dictionary → assessment rubric design → development plan → competency matrix.

## Specialist Agents

- `competency-architect`: Competency Architect. Defines competencies based on job analysis results, creates behavioral indicators, and designs proficiency level frameworks.
- `development-planner`: Competency Development Planner. Creates individual and organizational competency development plans based on gap analysis, and produces competency matrices.
- `job-analyst`: Job Analyst. Performs job description writing, core task analysis, and KSA (Knowledge, Skill, Attitude) extraction.
- `rubric-designer`: Assessment Rubric Designer. Designs assessment criteria, scoring guides, and assessment tools for each competency.

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
- `01_job_analysis.md` — Job analysis report
- `02_competency_dictionary.md` — Competency dictionary
- `03_assessment_rubric.md` — Assessment rubric
- `04_development_plan.md` — Competency development plan
- `05_competency_matrix.md` — Competency matrix

## Extension Skills

- `.agents/skills/bars-assessment/SKILL.md`
- `.agents/skills/ksa-taxonomy/SKILL.md`
