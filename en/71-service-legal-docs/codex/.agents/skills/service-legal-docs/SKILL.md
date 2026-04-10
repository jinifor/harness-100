---
name: service-legal-docs
description: >-
  Trigger when: the user wants the `service-legal-docs` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Service Legal Docs Harness

A service terms and legal document drafting agent team harness.

## Specialist Agents

- `consistency-reviewer`: consistency-reviewer specialist.
- `consumer-analyst`: consumer-analyst specialist.
- `privacy-specialist`: privacy-specialist specialist.
- `tos-specialist`: tos-specialist specialist.

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

- `.agents/skills/cross-document-linker/SKILL.md`
- `.agents/skills/unfair-terms-detector/SKILL.md`
