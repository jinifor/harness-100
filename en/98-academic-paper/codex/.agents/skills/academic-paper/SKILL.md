---
name: academic-paper
description: >-
  Trigger when: the user wants the `academic-paper` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Academic Paper Harness

An academic paper writing harness. An agent team collaborates to produce research design, experiment management, statistical analysis, paper writing, and submission preparation.

## Specialist Agents

- `experiment-manager`: Academic experiment manager. Develops experiment protocols, data collection procedures, instrument/survey design, and pilot test plans based on the research design.
- `paper-writer`: Academic paper writer. Writes scholarly papers following the IMRaD structure, adhering to academic writing conventions and managing citations.
- `research-designer`: Academic research designer. Formulates research questions, develops hypotheses, selects research methodology, defines variables, and analyzes prior literature.
- `statistical-analyst`: Academic statistical analyst. Develops statistical analysis strategies suited to the research design, generates analysis code, interprets results, and creates visualizations.
- `submission-preparer`: Academic paper submission preparer. Manages target journal selection, journal-specific formatting, cover letters, reviewer suggestions, and submission checklists.

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

- `.agents/skills/citation-standards/SKILL.md`
- `.agents/skills/research-methodology/SKILL.md`
