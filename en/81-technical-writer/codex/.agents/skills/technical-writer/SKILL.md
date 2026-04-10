---
name: technical-writer
description: >-
  Trigger when: the user wants the `technical-writer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Technical Writer Harness

technical document writing structuredesign→→diagram→review→versionmanagement A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `diagram-maker`: diagram writingspecialist. Mermaid grammaras diagram, when diagram, flowchart etc. technical document wheneach material creation.
- `doc-writer`: technical document specialist. information design according to body text writingand, code example and includedKorean nature also technical document creation.
- `info-architect`: information designspecialist. technical document reader analysisand, quality document structure and table of contents designand, document typeby template provide.
- `tech-reviewer`: technical reviewer(QA). document technicalquality accuracy, completeness, consistency, reader qualitynature verifyand specific revision feedback provide.
- `version-controller`: version managementspecialist. document data, change capability, version managementand, deployment preparation status confirm.

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

- `.agents/skills/api-doc-standards/SKILL.md`
- `.agents/skills/code-example-patterns/SKILL.md`
- `.agents/skills/diagram-patterns/SKILL.md`
