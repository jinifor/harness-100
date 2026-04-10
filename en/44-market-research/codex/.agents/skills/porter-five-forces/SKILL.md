---
name: porter-five-forces
description: >-
  Trigger when: the task needs `porter-five-forces` guidance as a focused standalone step or as part of the `market-research` harness. Do not trigger when: the user wants the full `market-research` pipeline or an unrelated task outside this skill's domain. Expected input: brief, draft, issue, or source material. Expected output: domain-specific guidance, patterns, checks, or revisions.
---

A skill that enhances industry structure analysis for the industry-analyst and competitor-analyst.

## Target Agents

- **industry-analyst** — Analyzes industry competitive dynamics
- **competitor-analyst** — Evaluates competitive positioning within industry structure

## The Five Forces Framework

### 1. Threat of New Entrants
```
Assessment factors:
- Capital requirements (High = low threat)
- Economies of scale (High = low threat)
- Brand loyalty / switching costs
- Access to distribution channels
- Government regulations / licenses
- Proprietary technology / patents
- Network effects

Rating: Low / Medium / High threat
```

### 2. Bargaining Power of Suppliers
```
Assessment factors:
- Number of suppliers (Few = high power)
- Switching costs to alternative suppliers
- Availability of substitutes
- Supplier concentration vs. industry
- Importance of volume to supplier
- Forward integration threat

Rating: Low / Medium / High power
```

### 3. Bargaining Power of Buyers
```
Assessment factors:
- Number of buyers (Few = high power)
- Buyer volume relative to total sales
- Switching costs for buyers
- Buyer price sensitivity
- Product differentiation
- Backward integration threat
- Access to market information

Rating: Low / Medium / High power
```

### 4. Threat of Substitute Products
```
Assessment factors:
- Availability of close substitutes
- Price-performance ratio of substitutes
- Buyer switching costs
- Buyer propensity to substitute
- Cross-industry substitutes

Rating: Low / Medium / High threat
```

### 5. Rivalry Among Existing Competitors
```
Assessment factors:
- Number and size of competitors
- Industry growth rate
- Product differentiation
- Exit barriers
- Fixed costs / value added
- Capacity utilization
- Competitive information availability

Rating: Low / Medium / High rivalry
```

## Analysis Output Template

```markdown
## Porter's Five Forces Analysis: [Industry]

### Summary
| Force | Rating | Key Factors |
|-------|--------|-------------|
| New Entrants | Low/Med/High | [Top 2-3 factors] |
| Supplier Power | Low/Med/High | [Top 2-3 factors] |
| Buyer Power | Low/Med/High | [Top 2-3 factors] |
| Substitutes | Low/Med/High | [Top 2-3 factors] |
| Rivalry | Low/Med/High | [Top 2-3 factors] |

### Overall Industry Attractiveness
[Assessment based on combined forces]

### Strategic Implications
1. [Implication + recommended action]
2. [Implication + recommended action]
3. [Implication + recommended action]
```

## Scoring Guide

```
Each force: 1 (Low) to 5 (High)
Industry Attractiveness Score = 25 - Sum of forces
  20-25: Very attractive
  15-19: Attractive
  10-14: Moderate
  5-9: Unattractive
```
