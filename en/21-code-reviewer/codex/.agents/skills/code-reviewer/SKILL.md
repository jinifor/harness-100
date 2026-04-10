---
name: code-reviewer
description: >-
  Trigger when: the user wants the `code-reviewer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Code Reviewer Harness

A harness where an agent team collaborates to perform automated code review across style, security, performance, and architecture.

## Specialist Agents

- `architecture-reviewer`: Architecture Reviewer. Analyzes design patterns, SOLID principles, dependency direction, coupling/cohesion, module structure, testability, and extensibility.
- `performance-analyst`: Code Performance Analyst. Analyzes time/space complexity, memory leaks, concurrency issues, DB query optimization, unnecessary computations, and caching opportunities.
- `review-synthesizer`: Code Review Synthesizer (QA). Synthesizes style, security, performance, and architecture review results; determines priorities and verifies cross-domain alignment.
- `security-analyst`: Code Security Analyst. Analyzes OWASP Top 10, injection vulnerabilities, authentication/authorization flaws, sensitive data exposure, insecure deserialization, and dependency vulnerabilities.
- `style-inspector`: Code Style Inspector. Inspects coding conventions, formatting, naming rules, comment quality, readability, and consistency. Proficient in language-specific style guides (PEP 8, Airbnb JS, Google Java, etc.).

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
- `01_style_review.md` — Code style review
- `02_security_review.md` — Security review
- `03_performance_review.md` — Performance review
- `04_architecture_review.md` — Architecture review
- `05_review_summary.md` — Comprehensive review report

## Extension Skills

- `.agents/skills/refactoring-catalog/SKILL.md`
- `.agents/skills/vulnerability-patterns/SKILL.md`
