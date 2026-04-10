# LLM App Builder Harness

This folder is the Codex version of the LLM App Builder Harness. Start with the local `llm-app-builder` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/llm-app-builder/SKILL.md`
- Specialist agents: `.codex/agents/deploy-engineer.toml`, `.codex/agents/eval-specialist.toml`, `.codex/agents/optimization-engineer.toml`, `.codex/agents/prompt-engineer.toml`, `.codex/agents/rag-architect.toml`
- Extension skills: `.agents/skills/chunking-strategy-guide/SKILL.md`, `.agents/skills/prompt-optimizer/SKILL.md`

## Workflow

- Start full-pipeline work with `llm-app-builder`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- LLM application construction: a harness where an agent team collaborates to perform prompt engineering → RAG architecture → optimization → evaluation → deployment.
