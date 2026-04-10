---
name: patent-drafter
description: >-
  Trigger when: the user wants the `patent-drafter` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Patent Drafter Harness

A patent application drafting agent team harness.

## Specialist Agents

- `claim-drafter`: Claim drafter. Designs optimal claim scope based on prior art search results and systematically drafts independent and dependent claims.
- `drawing-designer`: Drawing designer. Designs the drawing composition for patent specifications, defines detailed descriptions and reference numeral placement for each drawing. Creates text-based drawing specifications.
- `patent-reviewer`: Patent reviewer. Cross-verifies consistency between claims, specification, and drawings, and pre-checks for grounds of rejection from description deficiency, novelty, and inventive step perspectives.
- `prior-art-researcher`: Prior art researcher. Investigates existing patents, papers, and technical literature related to the invention, and analyzes differentiation points from novelty and inventive step perspectives.
- `specification-writer`: Specification writer. Writes a detailed description of the invention that fully supports the claims. Includes technical field, background art, problems to be solved, means for solving problems, effects of the invention, and embodiments.

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

- `.agents/skills/claim-drafting-patterns/SKILL.md`
- `.agents/skills/prior-art-search-strategy/SKILL.md`
