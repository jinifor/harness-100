---
name: cli-tool-builder
description: >-
  Trigger when: the user wants the `cli-tool-builder` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# CLI Tool Builder Harness

CLI tool construction: a harness where an agent team collaborates to perform command design → core development → testing → documentation → release.

## Specialist Agents

- `command-designer`: CLI command designer. Designs subcommand hierarchy, option/argument structure, and UX guidelines. Applies POSIX conventions and modern CLI best practices.
- `core-developer`: CLI core developer. Implements the command parser, handler functions, and business logic. Ensures clean architecture and testability.
- `docs-writer`: CLI documentation writer. Writes man pages, --help text, README, tutorials, and usage examples. Provides documentation that enables users to use the tool immediately.
- `release-engineer`: Release engineer. Configures the CLI tool's build, packaging, and deployment pipeline. Sets up deployment to PyPI/npm/Homebrew/GitHub Releases.
- `test-engineer`: CLI test engineer. Writes unit tests, integration tests, and E2E tests. Validates command combinations, error cases, and pipeline compatibility.

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

- `.agents/skills/arg-parser-generator/SKILL.md`
- `.agents/skills/ux-linter/SKILL.md`
