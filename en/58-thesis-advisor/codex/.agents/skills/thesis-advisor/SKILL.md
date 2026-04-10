---
name: thesis-advisor
description: >-
  Trigger when: the user wants the `thesis-advisor` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Thesis Advisor Harness

An agent team harness for thesis writing: topic selection, literature review, methodology, writing, and proofreading.

## Specialist Agents

- `literature-analyst`: Literature analyst. Systematically surveys prior research, critically reviews it, and constructs the theoretical framework for the study.
- `methodology-expert`: Research methodology expert. Designs research approaches, data collection methods, and analysis techniques appropriate to the research questions, and ensures methodological rigor.
- `proofreader`: Thesis proofreader. Performs grammar and spelling correction, academic format verification, consistency review, and plagiarism risk assessment.
- `topic-explorer`: Research topic explorer. Surveys trends in the research field, discovers research gaps, and formulates specific research questions and hypotheses.
- `writing-coach`: Thesis writing coach. Designs the overall structure of the thesis, drafts each chapter, and strengthens the argumentation.

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
- `01_topic_exploration.md` — Topic exploration report
- `02_literature_review.md` — Literature analysis report
- `03_methodology.md` — Methodology design document
- `04_writing_guide.md` — Writing guide
- `05_proofreading.md` — Proofreading report
- `06_review_report.md` — Review report

## Extension Skills

- `.agents/skills/academic-writing-style/SKILL.md`
- `.agents/skills/research-methodology/SKILL.md`
