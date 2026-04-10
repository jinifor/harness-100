---
name: cicd-pipeline
description: >-
  Trigger when: the user wants the `cicd-pipeline` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# CI/CD Pipeline Harness

A harness where an agent team collaborates to design, build, monitor, and optimize CI/CD pipelines.

## Specialist Agents

- `infra-engineer`: Infrastructure Engineer. Designs and implements CI/CD runner configuration, container builds (Dockerfile, docker-compose), environment variable/secret management, artifact repositories, and infrastructure provisioning (Terraform).
- `monitoring-specialist`: CI/CD Monitoring Specialist. Designs pipeline metrics (build time, success rate, deployment frequency), alert configuration (Slack, PagerDuty), dashboards, DORA metrics, and SLA/SLO.
- `pipeline-designer`: CI/CD Pipeline Designer. Designs build, test, security scan, and deployment stages; defines branch strategies (GitFlow, Trunk-based), trigger conditions, and per-environment deployment strategies (Blue-Green, Canary, Rolling).
- `pipeline-reviewer`: CI/CD Pipeline Reviewer (QA). Cross-validates pipeline efficiency, reliability, security, and design-implementation alignment.
- `security-scanner`: CI/CD Security Scanner. Integrates SAST (static analysis), DAST (dynamic analysis), SCA (dependency vulnerability), container image scanning, and secret detection into the pipeline.

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
- `01_pipeline_design.md` — Pipeline design document
- `02_pipeline_config/` — Pipeline configuration files (YAML, etc.)
- `03_monitoring.md` — Monitoring design document
- `04_security_scan.md` — Security scan configuration and report
- `05_review_report.md` — Pipeline review report

## Extension Skills

- `.agents/skills/deployment-strategies/SKILL.md`
- `.agents/skills/pipeline-security-gates/SKILL.md`
