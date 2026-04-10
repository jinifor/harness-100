# Harness 100

Production-grade harness collection with both original Claude Code assets and converted OpenAI Codex assets preserved side by side.

The repository contains **100 harness templates** across 10 domains, published in **English** and **Korean**. Each harness directory now stores:

- the original Claude-oriented source under `claude/.claude/`
- the converted Codex-oriented source under `codex/AGENTS.md`, `codex/.codex/`, and `codex/.agents/`

> **[English (en/)](en/)** | **[Korean (ko/)](ko/)**

## At a Glance

| Item | Count |
|---|---:|
| Harness templates | 100 |
| Language variants | 2 |
| Harness directories | 200 |
| Claude agent definitions | 978 |
| Claude skills | 630 |
| Codex custom agents | 978 |
| Codex skills | 630 |

## Repository Layout

Every harness now follows this nested archive layout:

```text
{NN}-{harness-name}/
├── claude/
│   └── .claude/
│       ├── CLAUDE.md
│       ├── agents/
│       │   └── *.md
│       └── skills/
│           └── */skill.md
└── codex/
    ├── AGENTS.md
    ├── .codex/
    │   └── agents/
    │       └── *.toml
    └── .agents/
        └── skills/
            └── */SKILL.md
```

## Quick Start

Copy the contents of the wrapper folder you want into your project root.

```bash
# Claude version
cp -r en/01-youtube-production/claude/. /path/to/my-project/

# Codex version
cp -r en/01-youtube-production/codex/. /path/to/my-project/

# Korean Codex version
cp -r ko/01-youtube-production/codex/. /path/to/my-project/
```

This preserves the required hidden paths such as `.claude`, `.codex`, and `.agents`.

## What This Repository Preserves

- Original Claude harness structure and source prompts
- Converted Codex `AGENTS.md`, custom-agent TOML, and skill layouts
- Domain-specific agent teams, workflows, deliverable contracts, and extension skills
- Parallel specialist decomposition across content, software, data, business, legal, education, and operations domains

## Quality Standards

Every harness includes:

- Original specialist workflow preserved from the Claude source
- Codex-facing `AGENTS.md`, custom agents, and reusable skills
- Structured output contracts and `_workspace/` deliverable conventions
- Task ordering with explicit dependencies and parallelizable stages
- Error handling and reduced-scope execution modes where the source defined them
- Trigger boundaries for generated Codex skills

## Categories

| # | Category | Harnesses | Highlights |
|---|----------|-----------|------------|
| 1 | Content Creation | 01-15 | YouTube, podcast, game narrative, comics, translation |
| 2 | Software Dev & DevOps | 16-30 | Full-stack, API, CI/CD, security audit, IaC |
| 3 | Data & AI/ML | 31-42 | ML experiments, NLP, RAG/LLM apps, design systems |
| 4 | Business & Strategy | 43-55 | Startup, market research, pricing, financial modeling |
| 5 | Education & Learning | 56-65 | Language tutor, exam prep, debate simulator, ADR |
| 6 | Legal & Compliance | 66-72 | Contracts, patents, GDPR/PIPA, regulatory filing |
| 7 | Health & Lifestyle | 73-80 | Meal planning, fitness, tax, travel, wedding |
| 8 | Communication & Docs | 81-88 | Technical writing, SOP, proposals, crisis comms |
| 9 | Operations & Process | 89-95 | Hiring, onboarding, audit, procurement |
| 10 | Specialized Domains | 96-100 | Real estate, e-commerce, ESG, IP portfolio |

### Dual-Format View

| Format | Primary Files | Intended Use |
|-------|---------------|--------------|
| **Claude** | `claude/.claude/CLAUDE.md`, `claude/.claude/agents/*.md`, `claude/.claude/skills/*/skill.md` | Preserve the original Claude Code harness source |
| **Codex** | `codex/AGENTS.md`, `codex/.codex/agents/*.toml`, `codex/.agents/skills/*/SKILL.md` | Use the converted OpenAI Codex harness source |

## Domain Expertise

| Domain | Embedded Frameworks |
|--------|-------------------|
| Content | AIDA, Pattern Interrupt, CURVE formula, Platform Specs |
| Development | SOLID, DDD, OWASP Top 10, Test Pyramid, DORA Metrics, CWE Top 25 |
| Data | Star/Snowflake Schema, Great Expectations, SHAP/LIME, Feature Engineering |
| Business | BMC, TAM/SAM/SOM, Porter's 5 Forces, RICE, Van Westendorp PSM |
| Education | Bloom's Taxonomy, ADDIE, CEFR, SM-2 Spaced Repetition, Toulmin Model |
| Legal | IRAC, MQM, GDPR/PIPA, IPC/CPC, Claim Drafting Patterns |
| Lifestyle | BMR/TDEE, ACSM Guidelines, Compound Interest, Route Optimization |
| Documents | Diataxis, PREP, STAR, MADR, SemVer, Mermaid Patterns |
| Operations | SIPOC/RACI, 4C Framework, SMART, NPS/CSAT, BARS Assessment |
| Specialized | GHG Protocol, Cap Rate/IRR, IMRaD, Georgia-Pacific, Double Materiality |

## License

Apache License 2.0 — See [LICENSE](LICENSE)
