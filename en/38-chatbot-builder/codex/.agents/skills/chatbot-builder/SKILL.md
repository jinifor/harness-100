---
name: chatbot-builder
description: >-
  Trigger when: the user wants the `chatbot-builder` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Chatbot Builder Harness

Chatbot construction: a harness where an agent team collaborates to perform intent analysis, conversation design, NLU development, integration, and testing.

## Specialist Agents

- `conversation-designer`: Conversation designer. Designs the chatbot's conversation scenarios, flowcharts, fallback strategies, and multi-turn dialog management. Builds a conversation structure that covers the entire user journey.
- `dialog-tester`: Dialog tester. Performs chatbot conversation scenario testing, edge case verification, persona consistency checks, and performance measurement. Serves as the quality gate.
- `integration-engineer`: Integration engineer. Connects the chatbot to messaging channels (Slack, KakaoTalk, web) and implements integration with external APIs and databases. Responsible for deployment and infrastructure.
- `nlu-developer`: NLU developer. Designs and implements the natural language understanding pipeline. Responsible for intent classification models, entity extraction, context management, and prompt engineering.
- `persona-architect`: Chatbot persona designer. Defines the bot's personality, speech style, tone and manner, and brand alignment. Establishes persona guidelines to ensure consistent user experience.

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

- `00_input.md` — User input summary
- `01_persona_spec.md` — Bot persona specification
- `02_conversation_design.md` — Conversation design document
- `03_nlu_config.md` — NLU configuration and training data
- `04_integration_spec.md` — Integration specification
- `05_test_report.md` — Test report
- `src/` — Chatbot source code

## Extension Skills

- `.agents/skills/conversation-flow-validator/SKILL.md`
- `.agents/skills/intent-taxonomy-builder/SKILL.md`
