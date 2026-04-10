# Operations Manual Harness

This folder is the Codex version of the Operations Manual Harness. Start with the local `operations-manual` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/operations-manual/SKILL.md`
- Specialist agents: `.codex/agents/document-analyst.toml`, `.codex/agents/faq-builder.toml`, `.codex/agents/flowchart-designer.toml`, `.codex/agents/manual-writer.toml`, `.codex/agents/training-producer.toml`
- Extension skills: `.agents/skills/flowchart-standards/SKILL.md`, `.agents/skills/knowledge-base-design/SKILL.md`

## Workflow

- Start full-pipeline work with `operations-manual`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An automated operations manual generation harness. An agent team collaborates to analyze existing documents/code and generate process flowcharts, step-by-step manuals, FAQs, and training materials.
