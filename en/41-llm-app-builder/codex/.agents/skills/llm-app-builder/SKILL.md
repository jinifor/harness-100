---
name: llm-app-builder
description: >-
  Trigger when: the user wants the `llm-app-builder` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# LLM App Builder Harness

LLM application construction: a harness where an agent team collaborates to perform prompt engineering → RAG architecture → optimization → evaluation → deployment.

## Specialist Agents

- `deploy-engineer`: LLM app deployment engineer. Configures production deployment including API server, scaling, monitoring, and guardrail runtime.
- `eval-specialist`: LLM evaluation specialist. Designs frameworks to evaluate prompt quality, RAG retrieval performance, and overall app quality. Builds benchmarks, A/B tests, and regression tests.
- `optimization-engineer`: LLM app optimization engineer. Optimizes the tradeoffs between cost, latency, and quality. Handles prompt compression, caching, model routing, and batch processing.
- `prompt-engineer`: Prompt engineer. Designs system prompts, few-shot examples, output formats, and guardrails for LLM apps. Ensures prompt stability and quality.
- `rag-architect`: RAG pipeline designer. Designs and implements the full RAG pipeline including document processing, chunking, embedding, vector store, retrieval, and reranking.

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

- `.agents/skills/chunking-strategy-guide/SKILL.md`
- `.agents/skills/prompt-optimizer/SKILL.md`
