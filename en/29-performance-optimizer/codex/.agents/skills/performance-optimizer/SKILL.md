---
name: performance-optimizer
description: >-
  Trigger when: the user wants the `performance-optimizer` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Performance Optimizer Harness

An agent team harness for performance optimization covering profiling, bottleneck analysis, optimization, and benchmarking.

## Specialist Agents

- `benchmark-manager`: benchmark administrator. performance test ·executionlower, optimization beforeafter  analysislower, performance regression lower CI integrated benchmark  .
- `bottleneck-analyst`: bottleneck analyst. profiling data as performance bottleneckof   peoplelower, impact scope calculatelower, optimization priority decision.
- `optimization-engineer`: optimization engineer. bottleneck analysis result as code, query, architecture countof optimization ·lower, optimization beforeafter   code provided.
- `perf-reviewer`: performance reviewer(QA). profiling-bottleneckanalysis-optimization-benchmark betweenof   verificationlower, performance regression risk evaluationlower, final report creation.
- `profiler`: performance profiler. CPU, memory, I/O, network for measurementlower, hotspot identificationlower, profiling data count·analysisto performance  -ize.

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
- `01_profiling_report.md` — Profiling results
- `02_bottleneck_analysis.md` — Bottleneck analysis report
- `03_optimization_plan.md` — Optimization plan and implementation
- `04_benchmark_results.md` — Benchmark results and comparison
- `05_review_report.md` — Review report

## Extension Skills

- `.agents/skills/caching-strategy-selector/SKILL.md`
- `.agents/skills/query-optimization-patterns/SKILL.md`
