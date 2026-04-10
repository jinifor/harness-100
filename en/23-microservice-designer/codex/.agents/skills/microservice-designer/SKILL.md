---
name: microservice-designer
description: >-
  Trigger when: the user wants the `microservice-designer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Microservice Designer Harness

An agent team harness for designing, decomposing, communicating, and monitoring microservice architectures. Automates the full pipeline from domain analysis to observability design.

## Specialist Agents

- `architecture-reviewer`: Microservice architecture reviewer (QA). Cross-validates consistency across domain, service, communication, and observability designs, and identifies potential risks in distributed systems.
- `communication-designer`: Inter-service communication design expert. Selects synchronous/asynchronous communication patterns, designs event buses, and configures API gateways and service meshes.
- `domain-analyst`: Domain analysis expert. Analyzes business domains from a DDD perspective, identifies bounded contexts, and derives domain events and aggregates through event storming.
- `observability-engineer`: Observability design expert. Establishes metrics, logging, and tracing strategies for distributed systems, and designs alerting rules and dashboards.
- `service-architect`: Microservice design expert. Maps bounded contexts to services, defines API contracts, and designs data ownership and deployment units.

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
- `01_domain_analysis.md` — Domain analysis report
- `02_service_design.md` — Service design document
- `03_communication_design.md` — Communication design document
- `04_observability_design.md` — Observability design document
- `05_review_report.md` — Final review report

## Extension Skills

- `.agents/skills/ddd-context-mapping/SKILL.md`
- `.agents/skills/distributed-patterns/SKILL.md`
