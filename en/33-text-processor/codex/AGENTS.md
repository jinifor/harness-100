# Text Processor Harness

This folder is the Codex version of the Text Processor Harness. Start with the local `text-processor` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/text-processor/SKILL.md`
- Specialist agents: `.codex/agents/classifier.toml`, `.codex/agents/extractor.toml`, `.codex/agents/preprocessor.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/sentiment-analyzer.toml`
- Extension skills: `.agents/skills/nlp-preprocessing-toolkit/SKILL.md`, `.agents/skills/sentiment-lexicon-builder/SKILL.md`

## Workflow

- Start full-pipeline work with `text-processor`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Text processing pipeline: a harness in which an agent team collaborates to transform bulk text into summaries, classifications, entity extractions, and sentiment analyses, producing structured data and reports.

## Deliverables

- `00_input.md` — User input and text source summary
- `01_preprocessing_result.md` — Preprocessing results and text statistics
- `02_classification_result.md` — Classification results
- `03_extraction_result.md` — Extraction results (entities, keywords, summaries)
- `04_sentiment_result.md` — Sentiment analysis results
- `05_final_report.md` — Final integrated report
- `structured_data/` — JSON/CSV structured data
