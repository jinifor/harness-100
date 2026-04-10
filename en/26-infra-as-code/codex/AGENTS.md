# Infra as Code Harness

This folder is the Codex version of the Infra as Code Harness. Start with the local `infra-as-code` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/infra-as-code/SKILL.md`
- Specialist agents: `.codex/agents/cost-optimizer.toml`, `.codex/agents/drift-detector.toml`, `.codex/agents/iac-reviewer.toml`, `.codex/agents/infra-architect.toml`, `.codex/agents/security-engineer.toml`
- Extension skills: `.agents/skills/cloud-cost-models/SKILL.md`, `.agents/skills/terraform-module-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `infra-as-code`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for Infrastructure as Code (IaC) design and implementation. Automates Terraform/Pulumi-based environment configuration, security, and cost optimization pipelines.

## Deliverables

- `00_input.md` — Organized user input
- `01_infra_design.md` — Infrastructure design document
- `02_security_design.md` — Security design document
- `03_cost_analysis.md` — Cost analysis report
- `04_drift_policy.md` — Drift detection policy
- `05_review_report.md` — Final review report
