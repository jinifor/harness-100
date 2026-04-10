---
name: customer-support
description: >-
  Trigger when: the user wants the `customer-support` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Customer Support Harness

Build a customer support system: an agent team collaborates to produce FAQ, response manuals, escalation policies, and analytics.

## Specialist Agents

- `cs-analyst`: CS analytics expert. Designs customer support performance metric systems, VOC (Voice of Customer) analysis frameworks, trend analysis, and service improvement proposals.
- `cs-reviewer`: Customer support system reviewer (QA). Cross-validates consistency across FAQ, response manual, escalation policy, and analytics, and evaluates system completeness from a customer experience perspective.
- `escalation-manager`: Escalation management expert. Designs tiered escalation policies, routing rules, SLAs, and crisis response protocols for customer inquiries.
- `faq-builder`: FAQ construction expert. Analyzes customer inquiry patterns to systematically build categorized FAQs, and designs structures for search optimization and self-service rate improvement.
- `response-specialist`: Response manual expert. Creates customer response scripts by situation, tone and manner guides, and emotional response protocols. Designs channel-specific (phone/chat/email) response systems.

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
- `01_faq.md` — FAQ document
- `02_response_manual.md` — Response manual
- `03_escalation_policy.md` — Escalation policy
- `04_cs_analytics.md` — CS analytics framework
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/csat-analyzer/SKILL.md`
- `.agents/skills/escalation-flowchart/SKILL.md`
