---
name: public-speaking
description: >-
  Trigger when: the user wants the `public-speaking` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Public Speaking Harness

comprehensive speechdocument→presentationversus→debatepreparationfrom→Q&Aexpectedanswer→rehearsalguide A harness where an agent team collaborates to produce deliverables.

## Specialist Agents

- `audience-analyst`: audience analysis. presentation/speech/debate target audience analysisand, context, expected, emotion status, companybefore degree level identifyto content strategy based .
- `debate-preparer`: debate preparation expert. presentationspecialist argument and, expected counterargument regarding buildingand, quality gapdocument strategy establish.
- `qa-strategist`: Q&A strategy. presentation after versusto expected question classificationand, each question regarding quality answer strategy and writing.
- `rehearsal-coach`: rehearsal value and cross-verification expert(QA). presentation delivercapability rehearsal guide writingand, speechdocument-debatepreparation-Q&A between consistency cross-verification.
- `speech-writer`: speech/presentation work. audience analysis basedas persuasioncapability basis00M speechdocument and presentation versus writing. numbercompanyquality technique and story utilization.

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

- `.agents/skills/audience-engagement/SKILL.md`
- `.agents/skills/rhetoric-patterns/SKILL.md`
