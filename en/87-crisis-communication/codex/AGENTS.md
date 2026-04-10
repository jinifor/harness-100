# Crisis Communication Harness

This folder is the Codex version of the Crisis Communication Harness. Start with the local `crisis-communication` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/crisis-communication/SKILL.md`
- Specialist agents: `.codex/agents/media-monitor.toml`, `.codex/agents/message-strategist.toml`, `.codex/agents/press-release-writer.toml`, `.codex/agents/qa-preparer.toml`, `.codex/agents/situation-analyst.toml`
- Extension skills: `.agents/skills/media-response-templates/SKILL.md`, `.agents/skills/stakeholder-mapping/SKILL.md`

## Workflow

- Start full-pipeline work with `crisis-communication`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- crisis situation occurrence when situationidentify→messagestrategy→press release→Q&A→monitoringto agent team to integration crisis package creation .
