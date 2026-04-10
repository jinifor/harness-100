---
name: infra-as-code
description: >-
  Trigger when: the user wants the `infra-as-code` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Infra as Code Harness

An agent team harness for Infrastructure as Code (IaC) design and implementation. Automates Terraform/Pulumi-based environment configuration, security, and cost optimization pipelines.

## Specialist Agents

- `cost-optimizer`: Cloud cost optimization expert. Optimizes infrastructure costs based on resource sizing, reserved instances, spot utilization, and FinOps culture.
- `drift-detector`: Drift detection expert. Detects differences between IaC state and actual infrastructure, verifies policy compliance, and establishes auto-remediation strategies.
- `iac-reviewer`: IaC reviewer (QA). Cross-validates consistency across design, security, cost, and drift, and verifies IaC best practices adherence.
- `infra-architect`: Infrastructure design expert. Designs cloud architecture, defines Terraform/Pulumi module structures, and establishes environment separation strategies and state management.
- `security-engineer`: Infrastructure security expert. Designs IAM policies, network security, data encryption, and compliance adherence, implementing security policies as code.

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
- `01_infra_design.md` — Infrastructure design document
- `02_security_design.md` — Security design document
- `03_cost_analysis.md` — Cost analysis report
- `04_drift_policy.md` — Drift detection policy
- `05_review_report.md` — Final review report

## Extension Skills

- `.agents/skills/cloud-cost-models/SKILL.md`
- `.agents/skills/terraform-module-patterns/SKILL.md`
