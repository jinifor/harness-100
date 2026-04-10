---
name: feedback-analyzer
description: >-
  Trigger when: the user wants the `feedback-analyzer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Feedback Analyzer Harness

A customer/employee feedback analysis harness. An agent team collaborates to handle everything from data collection through sentiment analysis, topic classification, trend detection, and insight reporting.

## Specialist Agents

- `data-collector`: Feedback data collection and cleansing expert. Integrates feedback from multiple channels (surveys, reviews, support logs, interviews), performs deduplication, normalization, and anonymization to build analysis-ready datasets.
- `insight-writer`: Insight report writing expert. Synthesizes sentiment analysis, topic classification, and trend results to produce tailored insight reports for executives and practitioners with specific action items.
- `sentiment-analyst`: Sentiment analysis expert. Determines positive/negative/neutral polarity of feedback text, scores emotional intensity, and analyzes sentiment changes over time.
- `topic-classifier`: Topic classification expert. Classifies feedback by semantic meaning, designs category systems, performs keyword clustering, tag mapping, and topic-by-sentiment cross-analysis.
- `trend-detector`: Trend analysis expert. Analyzes time-series patterns in feedback data to identify rising/falling trends, anomalies, seasonality, and event correlations.

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

- `.agents/skills/sentiment-scoring/SKILL.md`
- `.agents/skills/text-analytics-methods/SKILL.md`
