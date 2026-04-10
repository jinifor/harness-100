---
name: research-assistant
description: >-
  Trigger when: the user wants the `research-assistant` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Research Assistant Harness

An agent team harness for academic research assistance.

## Specialist Agents

- `critic-synthesizer`: Critical Analysis and Synthesis Specialist. Critically analyzes collected literature, identifies research gaps, and constructs the core narrative of the literature review through thematic synthesis.
- `literature-searcher`: Literature Search Specialist. Systematically explores academic databases and the web to collect papers, books, and reports related to the research topic, and evaluates their relevance.
- `note-taker`: Note-Taking Specialist. Reads each piece of literature thoroughly and organizes key arguments, methodology, major findings, and quotable passages into a structured format.
- `reference-manager`: Reference Management Specialist. Accurately manages bibliographic information for all cited sources, converts to requested citation formats (APA, MLA, Chicago, etc.), and verifies duplicates and omissions.
- `research-coordinator`: Research Coordinator (QA). Cross-verifies consistency across literature search, notes, critical analysis, and references, confirms research quality standards are met, and produces the final report.

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

- `.agents/skills/citation-formatter/SKILL.md`
- `.agents/skills/systematic-review-protocol/SKILL.md`
