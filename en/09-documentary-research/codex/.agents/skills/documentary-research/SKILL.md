---
name: documentary-research
description: >-
  Trigger when: the user wants the `documentary-research` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Documentary Research Harness

A harness where an agent team collaborates to produce documentary research, treatment plans, interview questions, and narration scripts.

## Specialist Agents

- `fact-checker`: Documentary fact checker (QA). Cross-verifies factual accuracy and consistency across research, treatment, interviews, and narration. Checks sources, logical errors, and bias, providing feedback.
- `interviewer`: Documentary interviewer. Designs customized questions per interviewee, and creates an interview guide including strategy, sequence, and follow-up questions.
- `narrator`: Documentary narrator. Writes narration scripts according to the treatment. Produces completed narration scripts including scene-by-scene tone, rhythm, emotional transitions, and fact delivery.
- `researcher`: Documentary researcher. Conducts in-depth research on the subject, collects statistics, compiles expert lists, analyzes historical context, and organizes references.
- `story-architect`: Documentary story architect. Converts research results into a 3-act treatment, designing scene division, narrative arc, emotion curves, and sequence structure.

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
- `01_research_brief.md` — Research brief
- `02_structure.md` — Treatment/structure design
- `03_interview_guide.md` — Interview guide
- `04_narration_script.md` — Narration script
- `05_review_report.md` — Fact-check/review report

## Extension Skills

- `.agents/skills/interview-design/SKILL.md`
- `.agents/skills/investigative-research/SKILL.md`
- `.agents/skills/narrative-structure/SKILL.md`
