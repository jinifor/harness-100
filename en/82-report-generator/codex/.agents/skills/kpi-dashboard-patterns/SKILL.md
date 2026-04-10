---
name: kpi-dashboard-patterns
description: >-
  Trigger when: the task needs `kpi-dashboard-patterns` guidance as a focused standalone step or as part of the `report-generator` harness. Do not trigger when: the user wants the full `report-generator` pipeline or an unrelated task outside this skill's domain. Expected input: brief, draft, issue, or source material. Expected output: domain-specific guidance, patterns, checks, or revisions.
---

analyst / executive-summarizer agent indicator analysis and dashboard composition tablelevel pattern.

## KPI framework (SMART-R)

| element | description | examplewhen |
|------|------|------|
| **S**pecific | specific target | "monthbetween specialist number" |
| **M**easurable | quality possible | peopleKorean figure (case, KRW, %) |
| **A**chievable | nature possibleKorean goal | beforeyear versus +20% |
| **R**elevant | goal and annual | sales → client secure → specialist |
| **T**ime-bound | duration specify | monthbetween, minutebasis, annualbetween |
| **R**esponsible | responsibilityspecialist/departmentfrom degree | team team |

## dashboard pattern

### pattern 1: management dashboard (Executive)

```
┌─────────────────────────────────────────┐
│ scorecard (core KPI 4~6items) │
│ [sales] [profit] [clientnumber] [NPS] │
├──────────────────┬──────────────────────┤
│ sales chart │ departmentdocumentby results chart │
│  │ (quality versus) │
├──────────────────┼──────────────────────┤
│ cost structure │ risk/issue │
│  │  │
└──────────────────┴──────────────────────┘
```

**principle**:
- →: summary→detailed (un-)
- scorecard: current + beforebasis + goal versus naturerate
- 1degree core, detailed 

### pattern 2: operations dashboard (Operational)

```
┌─────────────────────────────────────────┐
│ actualtime status (, error, time) │
├──────────┬──────────┬───────────────────┤
│ timeby │ dayby │ weekbetween trend │
│ │ comparison │ │
├──────────┴──────────┴───────────────────┤
│ /or more degree │
└─────────────────────────────────────────┘
```

## KPI analysis method

### minute analysis (Variance Analysis)

```
results vs goal minute:
 minute = results - goal
 minute = (results - goal) / goal × 100

minute etc.grade:
 🟢 ±5% within: 
 🟡 ±5~15%: week
 🔴 15% exceeding: → cause analysis required
```

### trend analysis

| analysis type | official | also |
|----------|------|------|
| MoM (beforemonth) | (month - beforemonth) / beforemonth × 100 | basis tax |
| YoY (beforeyear) | (month - beforeyear month) / beforeyear month × 100 | totalnature |
| CAGR | (final/initial)^(1/n) - 1 | basis naturerate |
| pyeongbalanced | Nduration pyeongbalanced | nature mitigation |

### analysis (Bridge Analysis)

```
beforebasis sales: 10000M
 (+) price person effect: +500M
 (+) increase: +1200M
 (-) exchange impact: -300M
 (-) to doperson increase: -200M
 (=) basis sales: 11200M
```

degree chart personby basis also visualization.

## scorecard design

### day KPI scorecard composition

```
┌──────────────────────┐
│ sales │ ← indicatorpeople
│ ₩145.200M │ ← current 
│ ▲ 12.3% vs beforemonth │ ← 
│ goal versus 96.8% │ ← naturerate
│ ████████░░ 96.8% │ ← 
└──────────────────────┘
```

### during KPI comparison

| KPI | results | goal | naturerate | tax |
|-----|------|------|--------|------|
| sales | 145.200M | 15000M | 96.8% | ↗ |
| profitrate | 12.3% | 15% | 82.0% | → |
| client | 1,234people | 1,000people | 123.4% | ↗ |
| NPS | 72 | 75 | 96.0% | ↘ |

## report typeby KPI tax

### monthbetween reporting

| category | core KPI | report KPI |
|---------|---------|---------|
| financial | sales, profit | salesKRW, EBITDA |
| client | client, rate | CAC, LTV, NPS |
| operations | nature, quality | rate, rate |
| personcompany | rate, hiring | trainingtime, also |

## quality checklist

| item | standard |
|------|------|
| KPI | SMART-R 6element |
| comparison standard | goal/beforebasis/competitor during 1items or more |
| direction | table/as i.e.when identify |
| day | chart within dayvalue |
| data standardday | data date specify |
| source | data whensystem specify |
