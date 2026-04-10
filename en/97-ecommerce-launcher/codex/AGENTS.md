# E-commerce Launcher Harness

This folder is the Codex version of the E-commerce Launcher Harness. Start with the local `ecommerce-launcher` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/ecommerce-launcher/SKILL.md`
- Specialist agents: `.codex/agents/cs-architect.toml`, `.codex/agents/detail-page-writer.toml`, `.codex/agents/marketing-manager.toml`, `.codex/agents/pricing-strategist.toml`, `.codex/agents/product-planner.toml`
- Extension skills: `.agents/skills/conversion-optimization/SKILL.md`, `.agents/skills/product-copy-formulas/SKILL.md`

## Workflow

- Start full-pipeline work with `ecommerce-launcher`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An e-commerce launch harness. An agent team collaborates to produce product planning, product detail pages, pricing strategy, marketing plans, and customer service architecture for online store launches.
