---
name: test-automation
description: >-
  Trigger when: 사용자가 `test-automation` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Test Automation Harness

테스트 자동화 전략 수립부터 테스트 작성, CI 통합, 커버리지 분석까지 에이전트 팀이 협업하는 하네스.

## Specialist Agents

- `coverage-analyst`: 커버리지 분석 전문가. 테스트 커버리지를 측정하고, 커버리지 갭을 식별하며, 리스크 기반으로 추가 테스트 우선순위를 결정한다.
- `integration-tester`: 통합 테스트 전문가. API, 데이터베이스, 외부 서비스 간의 상호작용을 검증하고, 테스트 환경 구성과 데이터 시딩 전략을 설계한다.
- `qa-reviewer`: 테스트 자동화 리뷰어(QA). 전략-테스트-커버리지 간의 정합성을 교차 검증하고, 테스트 품질과 유지보수성을 평가한다.
- `test-strategist`: 테스트 전략 수립 전문가. 테스트 피라미드를 기반으로 범위를 결정하고, 프레임워크/도구를 선정하며, CI 통합 전략과 품질 게이트를 설계한다.
- `unit-tester`: 단위 테스트 전문가. 비즈니스 로직의 단위 테스트를 작성하고, 모킹 전략을 설계하며, 경계값 분석과 동등 분할로 효과적인 테스트 케이스를 도출한다.

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
- `01_test_strategy.md` — 테스트 전략서
- `02_unit_tests.md` — 단위 테스트 코드 및 가이드
- `03_integration_tests.md` — 통합 테스트 코드 및 가이드
- `04_coverage_report.md` — 커버리지 분석 보고서
- `05_review_report.md` — 최종 리뷰 보고서

## 확장 스킬

- `.agents/skills/mocking-strategy/SKILL.md`
- `.agents/skills/test-design-patterns/SKILL.md`
