---
name: open-source-launcher
description: >-
  Trigger when: the user wants the `open-source-launcher` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Open Source Launcher Harness

An agent team harness for preparing open source project launches covering code cleanup, documentation, licensing, and community building.

## Specialist Agents

- `code-organizer`: code . open source items  code  , information removal,   -basedfor, dependency ,  system setup count.
- `community-manager`: community manager. project governance, Code of Conduct, this/PR template, CI/CD pipeline,  strategy, community  ·setup.
- `doc-writer`: documentation . README, CONTRIBUTING, API documentation, tutorial, CHANGELOG etc. open source projectin required-based documentation package .
- `launch-reviewer`: launching reviewer(QA). code-documentation-license-community betweenof   verificationlower, open source launching also evaluationlower, final list provided.
- `license-specialist`: license specialist. open source license , dependency license compatibility verification,  , CLA/DCO configuration count.

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
- `01_code_organization.md` — Code cleanup plan and results
- `02_documentation.md` — Documentation package (README, guides, etc.)
- `03_license_review.md` — License review and selection
- `04_community_setup.md` — Community setup and governance
- `05_launch_report.md` — Launch review report
- `generated_files/` — Generated files (README, LICENSE, CONTRIBUTING, etc.)

## Extension Skills

- `.agents/skills/community-health-metrics/SKILL.md`
- `.agents/skills/license-compatibility-matrix/SKILL.md`
