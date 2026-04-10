---
name: adr-writer
description: >-
  Trigger when: the user wants the `adr-writer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# ADR Writer Harness

An agent team harness for creating Architecture Decision Records (ADRs).

## Specialist Agents

- `adr-author`: ADR Document Author. Synthesizes context analysis, alternative research, and tradeoff evaluation results to produce a formal Architecture Decision Record in standard ADR format.
- `alternative-researcher`: Alternative Researcher. Explores technology options for architecture decisions and investigates each alternative's characteristics, maturity, community, and adoption cases, organizing them for comparison.
- `context-analyst`: Technical Context Analyst. Assesses the current system architecture, defines the problem requiring a decision, and identifies technical, organizational, and business constraints.
- `impact-tracker`: Impact Tracker. Analyzes the impact of architecture decisions on systems, teams, and processes, and establishes execution plans, migration roadmaps, and monitoring criteria.
- `tradeoff-evaluator`: Tradeoff Evaluator. Performs quantitative and qualitative comparison analysis between alternatives, generates weighted evaluation matrices by quality attribute, and recommends the optimal alternative.

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

- `.agents/skills/madr-template-engine/SKILL.md`
- `.agents/skills/quality-attribute-analyzer/SKILL.md`
