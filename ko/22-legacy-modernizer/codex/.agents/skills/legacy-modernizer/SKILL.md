---
name: legacy-modernizer
description: >-
  Trigger when: 사용자가 `legacy-modernizer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Legacy Modernizer Harness

레거시 코드베이스를 현대적 아키텍처로 전환하는 에이전트 팀 하네스. 분석→리팩토링전략→마이그레이션→검증 파이프라인을 자동화한다.

## Specialist Agents

- `legacy-analyzer`: 레거시 코드 분석 전문가. 코드베이스의 기술부채를 식별하고, 의존성 그래프를 매핑하며, 복잡도를 측정하여 현대화 대상의 우선순위를 결정한다.
- `migration-engineer`: 마이그레이션 실행 엔지니어. 리팩토링 전략에 따라 실제 코드 변환, API 현대화, 프레임워크 전환, 설정 외부화를 수행하고 마이그레이션 스크립트를 생성한다.
- `modernization-reviewer`: 현대화 프로젝트 리뷰어(QA). 분석-전략-마이그레이션-테스트 간의 일관성을 교차 검증하고, 누락·모순·위험을 발견하여 피드백을 제공한다.
- `refactoring-strategist`: 리팩토링 전략 수립 전문가. 레거시 분석 결과를 기반으로 최적의 리팩토링 패턴을 선정하고, 위험도-효과 매트릭스로 우선순위를 결정하며, 단계별 마이그레이션 로드맵을 설계한다.
- `regression-tester`: 회귀 테스트 전문가. 마이그레이션 전후 동작 보존을 검증하고, 성능 비교 벤치마크를 수행하며, 하위 호환성을 확인한다.

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
- `01_legacy_analysis.md` — 레거시 분석 보고서
- `02_refactoring_strategy.md` — 리팩토링 전략서
- `03_migration_plan.md` — 마이그레이션 실행 계획 및 코드
- `04_test_report.md` — 회귀 테스트 보고서
- `05_review_report.md` — 최종 리뷰 보고서

## 확장 스킬

- `.agents/skills/dependency-analysis/SKILL.md`
- `.agents/skills/strangler-fig-patterns/SKILL.md`
