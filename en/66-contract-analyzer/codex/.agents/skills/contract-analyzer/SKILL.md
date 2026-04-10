---
name: contract-analyzer
description: >-
  Trigger when: the user wants the `contract-analyzer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Contract Analyzer Harness

A contract analysis agent team harness.

## Specialist Agents

- `clause-analyst`: Clause analyst. Identifies the structure of contracts, analyzes the legal meaning, effect, and scope of each clause, and identifies missing essential clauses.
- `clause-drafter`: Clause drafting and revision expert. Writes standard contract clauses, proposes improvements to existing clauses, and designs clauses that protect the parties' interests.
- `comparison-reviewer`: Comparison reviewer. Compares contracts against industry standards, previous versions, or counterparty drafts to analyze differences and derive negotiation points.
- `contract-coordinator`: Contract coordinator (QA). Synthesizes clause analysis, amendments, risk assessment, and comparison review to produce a final legal opinion and verify consistency across deliverables.
- `risk-assessor`: Risk assessor. Identifies legal and business risks in contracts, discovers disadvantageous clauses, and presents risk mitigation strategies.

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

- `.agents/skills/clause-risk-database/SKILL.md`
- `.agents/skills/negotiation-playbook/SKILL.md`
