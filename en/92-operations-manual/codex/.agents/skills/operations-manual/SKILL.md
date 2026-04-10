---
name: operations-manual
description: >-
  Trigger when: the user wants the `operations-manual` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Operations Manual Harness

An automated operations manual generation harness. An agent team collaborates to analyze existing documents/code and generate process flowcharts, step-by-step manuals, FAQs, and training materials.

## Specialist Agents

- `document-analyst`: Existing document, code, and wiki analysis expert. Extracts current business processes from organizational assets, converts tacit knowledge into explicit knowledge, and creates glossaries and process inventories.
- `faq-builder`: FAQ and troubleshooting guide expert. Anticipates questions and problems that arise during work execution and creates FAQs, troubleshooting decision trees, and escalation guides.
- `flowchart-designer`: Process flowchart design expert. Visualizes business processes as Mermaid diagrams and creates complete process maps including branching logic, parallel processing, and exception flows.
- `manual-writer`: Step-by-step operations manual writing expert. Creates procedures, checklists, and screenshot guides that anyone can follow based on process analysis results.
- `training-producer`: Training material production expert. Transforms manual content into learning-objective-based training materials, generating quizzes, hands-on exercises, summary cards, and onboarding checklists.

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

- `.agents/skills/flowchart-standards/SKILL.md`
- `.agents/skills/knowledge-base-design/SKILL.md`
