---
name: performance-optimizer
description: >-
  Trigger when: 사용자가 `performance-optimizer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Performance Optimizer Harness

성능 최적화의 프로파일링→병목분석→최적화→벤치마크를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `benchmark-manager`: 벤치마크 관리자. 성능 테스트를 설계·실행하고, 최적화 전후를 비교 분석하며, 성능 회귀를 방지하는 CI 통합 벤치마크 체계를 구축한다.
- `bottleneck-analyst`: 병목 분석가. 프로파일링 데이터를 기반으로 성능 병목의 근본 원인을 규명하고, 영향 범위를 산정하며, 최적화 우선순위를 결정한다.
- `optimization-engineer`: 최적화 엔지니어. 병목 분석 결과를 기반으로 코드, 쿼리, 아키텍처 수준의 최적화를 설계·구현하고, 최적화 전후 비교를 위한 코드를 제공한다.
- `perf-reviewer`: 성능 리뷰어(QA). 프로파일링-병목분석-최적화-벤치마크 간의 정합성을 교차 검증하고, 성능 회귀 위험을 평가하며, 최종 보고서를 생성한다.
- `profiler`: 성능 프로파일러. CPU, 메모리, I/O, 네트워크 사용량을 측정하고, 핫스팟을 식별하며, 프로파일링 데이터를 수집·분석하여 성능 현황을 가시화한다.

## Workflow

1. 사용자 요청, 제약 조건, 기존 자료를 정리한다.
2. 필요하면 `_workspace/00_input.md`에 시작 컨텍스트를 저장한다.
3. 요청 범위에 맞는 specialist를 순차 또는 병렬로 실행하고, 번호가 매겨진 `_workspace/` 산출물로 handoff 한다.
4. 리뷰어 또는 종합 검토 specialist가 있으면 마지막에 전체 결과를 검증한다.
5. 누락된 단계, 한계, 재사용한 입력 파일을 최종 보고에 명시한다.

## 작업 규칙

- source `.claude` 파일은 수정하지 않는다.
- 모든 하네스 산출물은 `_workspace/`에 유지한다.
- 기존 파일이 이미 있으면 적절한 위치에 복사하거나 참조하고 중복 단계를 건너뛸 수 있다.
- 외부 조회나 생성이 실패해도 가능한 범위까지 진행하고 한계를 적는다.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_profiling_report.md` — 프로파일링 결과
- `02_bottleneck_analysis.md` — 병목 분석 보고서
- `03_optimization_plan.md` — 최적화 계획 및 구현
- `04_benchmark_results.md` — 벤치마크 결과 및 비교
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/caching-strategy-selector/SKILL.md`
- `.agents/skills/query-optimization-patterns/SKILL.md`
