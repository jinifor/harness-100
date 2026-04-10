# Chatbot Builder Harness

This folder is the Codex version of the Chatbot Builder Harness. Start with the local `chatbot-builder` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/chatbot-builder/SKILL.md`
- Specialist agents: `.codex/agents/conversation-designer.toml`, `.codex/agents/dialog-tester.toml`, `.codex/agents/integration-engineer.toml`, `.codex/agents/nlu-developer.toml`, `.codex/agents/persona-architect.toml`
- Extension skills: `.agents/skills/conversation-flow-validator/SKILL.md`, `.agents/skills/intent-taxonomy-builder/SKILL.md`

## Workflow

- Start full-pipeline work with `chatbot-builder`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- Chatbot construction: a harness where an agent team collaborates to perform intent analysis, conversation design, NLU development, integration, and testing.

## Deliverables

- `00_input.md` — User input summary
- `01_persona_spec.md` — Bot persona specification
- `02_conversation_design.md` — Conversation design document
- `03_nlu_config.md` — NLU configuration and training data
- `04_integration_spec.md` — Integration specification
- `05_test_report.md` — Test report
- `src/` — Chatbot source code
