---
name: negotiation-playbook
description: >-
  Trigger when: the task needs `negotiation-playbook` guidance as a focused standalone step or as part of the `contract-analyzer` harness. Do not trigger when: the user wants the full `contract-analyzer` pipeline or an unrelated task outside this skill's domain. Expected input: brief, draft, issue, or source material. Expected output: domain-specific guidance, patterns, checks, or revisions.
---

Provides clause-level negotiation strategies, alternative wording templates, and concession-exchange matrices.

## Basic Negotiation Framework: BATNA-ZOPA Analysis

### Negotiating Power Diagnosis Formula

```
negotiating_power = (alternative_strength x 0.3) + (time_flexibility x 0.2) + (information_advantage x 0.2) + (market_position x 0.3)

Each item on a 1-10 scale

Result: 8-10 Aggressive | 5-7 Balanced | 1-4 Defensive, focus on essentials
```

### Concession-Exchange Matrix

| Concession Difficulty | Important to Us | Important to Them | Strategy |
|----------------------|----------------|-------------------|----------|
| Easy Concession | Low | High | Concede first as a goodwill gesture |
| Exchange Card | High | High | Conditional exchange |
| Must-Hold Item | High | Low | Non-negotiable |
| Irrelevant Item | Low | Low | Agree quickly |

## Clause-Level Negotiation Strategies and Alternative Wording

### Damages — Graduated Concession Plan

**Party B Perspective (Liability Limitation)**
```
Original: "Party B shall indemnify all damages"
-> Step 1: "Limited to direct and ordinary damages, with total liability capped at 100% of contract value"
-> Step 2: "Cap at last 12 months of payments, excluding indirect and consequential damages"
-> Step 3: "Within the scope of milestone payments for the relevant deliverable, burden of proof on Party A"
```

### Intellectual Property — Amendment Strategy

| Original | Risk | Amendment | Negotiation Point |
|----------|------|-----------|-------------------|
| All deliverables vest in Party A | Total IP loss | License within scope of Party A's purpose | "Generic modules retained by Party B" |
| Transfer including source code | Cannot pursue subsequent business | Executable delivery + escrow | "Business continuity assurance" |
| Transfer including third-party SW | License violation | Explicitly exclude third-party SW | "Open source conditions disclosure" |

### Termination Clause — Balanced Template

```
Article X (Termination)
1. Either party may terminate with [30/60] days written notice.
2. In case of material breach, immediate termination after [14]-day cure notice if not remedied.
3. Payment settlement for work performed upon termination.
4. Confidentiality, damages, and IP clauses survive termination.
```

### Payment — Leverage Strategy

| Current Terms | Improvement | Exchange Offer |
|--------------|-------------|----------------|
| 60 days after completion | Monthly milestone payments | "2% discount on milestone payments" |
| 30 days after acceptance | Acceptance period limited to 14 days | "Add deemed acceptance clause" |
| Lump sum post-delivery | 30% advance + 40% interim + 30% balance | "Performance bond for advance payment" |

## Negotiation Communication 4-Step Structure

```
[1] Gratitude + Relationship Affirmation
"We look forward to a successful partnership."

[2] Specific Concern (Objective Basis)
"Based on industry standard practices and case law, we have concerns."

[3] Alternative Proposal (Emphasize Mutual Benefit)
"This proposal achieves Party A's protection goals while addressing Party B's concerns."

[4] Signal Flexibility
"We are open to discussing alternative approaches."
```

## BATNA Deployment When Negotiations Stall

```
"We are unable to obtain internal approval under the current terms.
If we can reach agreement on [3 key clauses], we can accept your position on the remainder."
```

## Negotiation Outcome Evaluation

```
result = sum(improvement_per_clause x importance) / sum(importance)
improvement: Original maintained 0 | Partial improvement 50 | Alternative reflected 80 | Fully achieved 100
outcome: 80+ Excellent | 60-79 Good | 40-59 Average | Under 40 Renegotiation recommended
```

## Unfair Terms Review Criteria

| Type | Criterion | Legal Basis |
|------|----------|-------------|
| Indemnification Clause | Cannot exempt intentional/negligent acts by provider | Standard Terms Act, Article 7 |
| Damages Limitation | Cannot unreasonably limit consumer claims | Standard Terms Act, Article 7 |
| Cancellation/Termination | Cannot unreasonably limit consumer's right to cancel | Standard Terms Act, Article 9 |
| Jurisdiction Agreement | Cannot impose unfavorable exclusive jurisdiction on consumer | Standard Terms Act, Article 14 |

## Notes

- Reflects fair trade commission unfair terms review guidelines
- Detailed cases: See `references/negotiation-cases.md`
