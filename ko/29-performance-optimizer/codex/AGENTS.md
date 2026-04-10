# Performance Optimizer Harness Codex 지침

## 목적

- 이 디렉토리는 `Performance Optimizer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/performance-optimizer/SKILL.md`
- 전문 agent: `.codex/agents/benchmark-manager.toml`, `.codex/agents/bottleneck-analyst.toml`, `.codex/agents/optimization-engineer.toml`, `.codex/agents/perf-reviewer.toml`, `.codex/agents/profiler.toml`
- 확장 스킬: `.agents/skills/caching-strategy-selector/SKILL.md`, `.agents/skills/query-optimization-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `performance-optimizer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 성능 최적화의 프로파일링→병목분석→최적화→벤치마크를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_profiling_report.md` — 프로파일링 결과
- `02_bottleneck_analysis.md` — 병목 분석 보고서
- `03_optimization_plan.md` — 최적화 계획 및 구현
- `04_benchmark_results.md` — 벤치마크 결과 및 비교
- `05_review_report.md` — 리뷰 보고서
