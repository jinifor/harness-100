# Performance Optimizer Harness

This folder is the Codex version of the Performance Optimizer Harness. Start with the local `performance-optimizer` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/performance-optimizer/SKILL.md`
- Specialist agents: `.codex/agents/benchmark-manager.toml`, `.codex/agents/bottleneck-analyst.toml`, `.codex/agents/optimization-engineer.toml`, `.codex/agents/perf-reviewer.toml`, `.codex/agents/profiler.toml`
- Extension skills: `.agents/skills/caching-strategy-selector/SKILL.md`, `.agents/skills/query-optimization-patterns/SKILL.md`

## Workflow

- Start full-pipeline work with `performance-optimizer`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for performance optimization covering profiling, bottleneck analysis, optimization, and benchmarking.

## Deliverables

- `00_input.md` — Organized user input
- `01_profiling_report.md` — Profiling results
- `02_bottleneck_analysis.md` — Bottleneck analysis report
- `03_optimization_plan.md` — Optimization plan and implementation
- `04_benchmark_results.md` — Benchmark results and comparison
- `05_review_report.md` — Review report
