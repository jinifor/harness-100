---
name: translation-localization
description: >-
  Trigger when: the user wants the `translation-localization` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Translation & Localization Harness

A harness where an agent team collaborates to perform multilingual translation, localization, cultural adaptation, and terminology management.

## Specialist Agents

- `localizer`: Localization expert. Adapts translated text to the cultural context of the target market. Handles idioms, metaphors, units of measurement, currency, date/time formats, and cultural sensitivities.
- `quality-reviewer`: Translation quality reviewer (QA). Systematically verifies translation accuracy, fluency, terminology consistency, and localization suitability, calculating MQM-based quality scores.
- `style-harmonizer`: Style harmonizer. Maintains consistent tone and voice, writing style, and formality level throughout the translation. Applies brand voice appropriately to the target language.
- `terminology-manager`: Terminology Management. Translation toof Glossary(Glossary) ·and, before Terminologyof Translation ensure. Industry standards Terminologyand Terminology manage.
- `translator`: before Translation. Source textof of, Nuance, context Analysisand Target languageto naturally . of, Source textof ofand Preservation Translation perform.

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
- `01_source_analysis.md` — Source analysis/translation strategy
- `02_terminology.md` — Glossary
- `03_translation.md` — Translated text
- `04_localization.md` — Localization applied results
- `05_review_report.md` — Quality review report

## Extension Skills

- `.agents/skills/cultural-adaptation-guide/SKILL.md`
- `.agents/skills/translation-quality-mqm/SKILL.md`
