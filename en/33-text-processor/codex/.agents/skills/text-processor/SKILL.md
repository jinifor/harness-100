---
name: text-processor
description: >-
  Trigger when: the user wants the `text-processor` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Text Processor Harness

Text processing pipeline: a harness in which an agent team collaborates to transform bulk text into summaries, classifications, entity extractions, and sentiment analyses, producing structured data and reports.

## Specialist Agents

- `classifier`: Text classification engine. Performs topic classification, intent classification, multi-label tagging, and document type identification. Automatically designs classification taxonomies or applies user-defined schemes.
- `extractor`: Information extraction specialist. Performs named entity recognition (NER), keyword extraction, relation extraction, and automatic summarization to extract structured information from unstructured text.
- `preprocessor`: Text preprocessing specialist. Performs noise removal, tokenization, normalization, language detection, sentence segmentation, and encoding handling on raw text to prepare it for downstream NLP tasks.
- `report-writer`: Text processing report writing specialist. Integrates preprocessing, classification, extraction, and sentiment analysis results to produce a final report centered on actionable business insights.
- `sentiment-analyzer`: Sentiment analysis specialist. Performs polarity analysis (positive/negative/neutral), emotion classification (joy/anger/sadness, etc.), aspect-based sentiment analysis (by product feature), and opinion mining.

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

- `00_input.md` — User input and text source summary
- `01_preprocessing_result.md` — Preprocessing results and text statistics
- `02_classification_result.md` — Classification results
- `03_extraction_result.md` — Extraction results (entities, keywords, summaries)
- `04_sentiment_result.md` — Sentiment analysis results
- `05_final_report.md` — Final integrated report
- `structured_data/` — JSON/CSV structured data

## Extension Skills

- `.agents/skills/nlp-preprocessing-toolkit/SKILL.md`
- `.agents/skills/sentiment-lexicon-builder/SKILL.md`
