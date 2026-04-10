---
name: knowledge-base-builder
description: >-
  Trigger when: the user wants the `knowledge-base-builder` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Knowledge Base Builder Harness

An agent team harness for building organizational knowledge management systems.

## Specialist Agents

- `knowledge-collector`: Knowledge Collector. Systematically extracts knowledge from diverse sources within the organization including documents, codebases, processes, and tacit knowledge, and builds an inventory.
- `maintenance-planner`: Maintenance Planner. Establishes governance models, update cycles, quality management processes, and contribution guidelines to ensure the long-term quality of the knowledge base.
- `search-optimizer`: Search Optimizer. Optimizes the knowledge base for search by designing search indexes, synonym mappings, popular query optimization, and findability improvements.
- `taxonomy-designer`: Taxonomy Designer. Designs the information architecture for structuring knowledge, including category systems, tag schemes, navigation structures, and search optimization.
- `wiki-builder`: Wiki Builder. Transforms extracted knowledge items into actual wiki articles following templates and writing guidelines to build the knowledge base content.

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

- `.agents/skills/content-lifecycle-manager/SKILL.md`
- `.agents/skills/information-architecture/SKILL.md`
