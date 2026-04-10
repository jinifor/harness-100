# Mobile App Builder Harness

This folder is the Codex version of the Mobile App Builder Harness. Start with the local `mobile-app-builder` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/mobile-app-builder/SKILL.md`
- Specialist agents: `.codex/agents/api-integrator.toml`, `.codex/agents/app-developer.toml`, `.codex/agents/qa-engineer.toml`, `.codex/agents/store-manager.toml`, `.codex/agents/ux-designer.toml`
- Extension skills: `.agents/skills/app-store-optimization/SKILL.md`, `.agents/skills/mobile-ux-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `mobile-app-builder`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- A harness where an agent team collaborates to perform UI/UX design, native code generation, API integration, and store deployment preparation for mobile apps.

## Deliverables

- `00_input.md` — Organized user input
- `01_ux_design.md` — UX/UI design document
- `02_app_code/` — App source code
- `02_app_architecture.md` — App architecture document
- `03_api_integration.md` — API integration specification
- `04_store_listing.md` — Store deployment metadata
- `05_qa_report.md` — QA verification report
