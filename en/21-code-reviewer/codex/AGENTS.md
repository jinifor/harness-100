# Code Reviewer Harness

This folder is the Codex version of the Code Reviewer Harness. Start with the local `code-reviewer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/code-reviewer/SKILL.md`
- Specialist agents: `.codex/agents/architecture-reviewer.toml`, `.codex/agents/performance-analyst.toml`, `.codex/agents/review-synthesizer.toml`, `.codex/agents/security-analyst.toml`, `.codex/agents/style-inspector.toml`
- Extension skills: `.agents/skills/refactoring-catalog/SKILL.md`, `.agents/skills/vulnerability-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `code-reviewer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to perform automated code review across style, security, performance, and architecture.

## Deliverables

- `00_input.md` — Organized user input
- `01_style_review.md` — Code style review
- `02_security_review.md` — Security review
- `03_performance_review.md` — Performance review
- `04_architecture_review.md` — Architecture review
- `05_review_summary.md` — Comprehensive review report
