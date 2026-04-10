---
name: debate-simulator
description: >-
  Trigger when: the user wants the `debate-simulator` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Debate Simulator Harness

An agent team harness for debate simulation.

## Specialist Agents

- `con-debater`: Con-side debater. Systematically constructs arguments against the resolution and prepares rebuttals of the pro side's claims.
- `judge`: Debate judge. Fairly evaluates both sides' arguments, renders a verdict according to evaluation criteria, and provides educational feedback.
- `pro-debater`: Pro-side debater. Systematically constructs arguments for the affirmative position and prepares rebuttals against anticipated counterarguments.
- `rapporteur`: Rapporteur. Summarizes the entire debate, presents both sides' arguments in a balanced manner, and produces a comprehensive report with key insights.
- `topic-analyst`: Debate topic analyst. Structures the issues within a topic, identifies core points of contention, and designs the debate framework.

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
- `01_topic_analysis.md` — Topic analysis
- `02_pro_arguments.md` — Pro-side arguments
- `03_con_arguments.md` — Con-side arguments
- `04_verdict.md` — Verdict
- `05_debate_record.md` — Debate record
- `06_review_report.md` — Review report

## Extension Skills

- `.agents/skills/argumentation-framework/SKILL.md`
- `.agents/skills/logical-fallacy-detector/SKILL.md`
