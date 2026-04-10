---
name: steep-framework
description: >-
  Trigger when: the task needs `steep-framework` guidance as a focused standalone step or as part of the `scenario-planner` harness. Do not trigger when: the user wants the full `scenario-planner` pipeline or an unrelated task outside this skill's domain. Expected input: brief, draft, issue, or source material. Expected output: domain-specific guidance, patterns, checks, or revisions.
---

A specialized skill that enhances the environmental scanning capabilities of the variable-analyst agent.

## Target Agent

- **variable-analyst** — Systematic identification of key variables using the STEEP framework

## STEEP 6-Dimension Scanning

### Dimension Definitions

| Dimension | Scope | Example Variables |
|-----------|-------|-------------------|
| **S** Social | Demographics, lifestyle, values, education | Aging population, remote work adoption, DEI awareness |
| **T** Technological | Innovation, adoption rate, disruption | AI adoption, quantum computing, cybersecurity threats |
| **E** Economic | Growth, inflation, trade, labor market | Interest rate changes, supply chain restructuring, gig economy |
| **E** Environmental | Climate, resources, sustainability | Carbon regulation, ESG pressure, resource scarcity |
| **P** Political | Government policy, regulation, geopolitics | Data privacy regulation, trade wars, political polarization |
| **L** Legal | Laws, compliance, intellectual property | Antitrust regulation, labor law changes, patent disputes |

### Scanning Checklist per Dimension

For each dimension, investigate:
1. **Current State**: What is happening now?
2. **Direction of Change**: Which way is the trend moving?
3. **Speed of Change**: How fast? (Gradual/Rapid/Discontinuous)
4. **Certainty**: Is this predetermined or uncertain?
5. **Impact**: How does it affect our industry/organization?

## Uncertainty-Impact Matrix

### 4-Quadrant Classification

```
Impact (High)
    |  Q2: Predetermined     Q1: Scenario Drivers
    |  (Certain Trends)      (Matrix Axes)
    |  → Apply to all        → 2 axes for matrix
    |    scenarios
    |
    |  Q4: Background         Q3: Monitor
    |  (Ignore)               (Wild Cards)
    |  → Minimal attention    → Watch list
    |
Impact (Low)
    +--- Uncertainty (Low) ---- Uncertainty (High)
```

### Assessment Criteria

| Score | Uncertainty | Impact |
|-------|-----------|--------|
| 5 | Completely unpredictable, multiple possible outcomes | Existential impact on business model |
| 4 | Difficult to predict, 2-3 plausible outcomes | Significant impact on core revenue |
| 3 | Somewhat predictable but variable | Moderate impact on operations |
| 2 | Mostly predictable with minor variations | Limited departmental impact |
| 1 | Nearly certain, single expected outcome | Negligible impact |

## Trend Classification

### Predetermined Trends
- High certainty of direction (uncertainty score 1-2)
- Applied as constants across all scenarios
- Example: Aging population in developed nations

### Critical Uncertainties
- High uncertainty AND high impact (Q1 quadrant)
- Used as scenario matrix axes
- Example: AI regulation direction (restrictive vs. permissive)

### Wild Cards
- Low probability but potentially high impact events
- Included as shock events within specific scenarios
- Example: Pandemic, technology breakthrough, geopolitical crisis
