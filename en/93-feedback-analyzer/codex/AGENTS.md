# Feedback Analyzer Harness

This folder is the Codex version of the Feedback Analyzer Harness. Start with the local `feedback-analyzer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/feedback-analyzer/SKILL.md`
- Specialist agents: `.codex/agents/data-collector.toml`, `.codex/agents/insight-writer.toml`, `.codex/agents/sentiment-analyst.toml`, `.codex/agents/topic-classifier.toml`, `.codex/agents/trend-detector.toml`
- Extension skills: `.agents/skills/sentiment-scoring/SKILL.md`, `.agents/skills/text-analytics-methods/SKILL.md`

## Workflow

- Start full-pipeline work with `feedback-analyzer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A customer/employee feedback analysis harness. An agent team collaborates to handle everything from data collection through sentiment analysis, topic classification, trend detection, and insight reporting.
