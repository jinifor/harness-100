---
name: regulatory-filing
description: >-
  Trigger when: the user wants the `regulatory-filing` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Regulatory Filing Harness

A regulatory filing and permit application agent team harness.

## Specialist Agents

- `attachment-preparer`: attachment-preparer specialist.
- `document-drafter`: document-drafter specialist.
- `requirements-investigator`: requirements-investigator specialist.
- `submission-verifier`: submission-verifier specialist.

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

- `.agents/skills/form-filling-guide/SKILL.md`
- `.agents/skills/permit-requirements-db/SKILL.md`
