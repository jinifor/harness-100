---
name: sop-writer
description: >-
  Trigger when: the user wants the `sop-writer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# SOP Writer Harness

standard operating procedure(SOP) processanalysis→procedure document→checklist→training materials→versionmanagement A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `checklist-designer`: SOP checklist designspecialist. procedure document core stage execution inspectiontable exchangeand, quality , dayday/weekbetween/monthbetween inspection checklist design.
- `procedure-writer`: SOP procedure document writingspecialist. process analysis result basedas according toto do number peopleKorean stageby procedure document writing. ISO/ requirement department document applied.
- `process-analyst`: SOP process analysis. current work flow systematicas analysisand, input/capability/relatedspecialist/examplesituation identificationto procedure document writing based .
- `training-developer`: SOP training materials workspecialist. procedure document and checklist basedas personcapability to do number training guide, scenario annual, assessment document work.
- `version-controller`: SOP version management and cross-verification expert(QA). procedure document-checklist-training materials between consistency cross-verificationand, document version management total establish.

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

## Extension Skills

- `.agents/skills/checklist-design/SKILL.md`
- `.agents/skills/process-mapping/SKILL.md`
