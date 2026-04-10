---
name: scenario-planner
description: >-
  Trigger when: 사용자가 `scenario-planner` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Scenario Planner Harness

불확실한 환경에서 핵심 변수를 정의하고, 시나리오 매트릭스를 구성하여 영향 분석과 대응 전략을 수립하는 에이전트 팀 하네스.

## Specialist Agents

- `impact-assessor`: 시나리오별 영향 평가 전문가. 각 시나리오가 조직의 전략, 재무, 운영, 인력에 미치는 정량적·정성적 영향을 분석하고, 리스크와 기회를 체계적으로 평가한다.
- `integration-reviewer`: 시나리오 기획 통합 리뷰어(QA). 변수 분석-시나리오 매트릭스-영향 분석-대응 전략 간의 논리적 정합성을 교차 검증하고, 최종 의사결정 문서를 통합 편집한다.
- `scenario-designer`: 시나리오 매트릭스 설계자. 핵심 변수 축을 기반으로 2x2 또는 3x3 시나리오 매트릭스를 구성하고, 각 시나리오의 서사(narrative)와 전개 경로를 작성한다.
- `strategy-architect`: 대응 전략 수립 전문가. 시나리오별 영향 분석 결과를 바탕으로 로버스트 전략, 헤지 전략, 옵션 전략을 설계하고 통합 의사결정 문서를 작성한다.
- `variable-analyst`: 시나리오 기획의 핵심 변수 분석가. 의사결정에 영향을 미치는 핵심 불확실성 변수를 식별하고, 변수 간 상관관계를 분석하여 시나리오 축을 결정한다.

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
- `01_variable_analysis.md` — 핵심 변수 분석서
- `02_scenario_matrix.md` — 시나리오 매트릭스 및 서사
- `03_impact_assessment.md` — 영향 분석 보고서
- `04_response_strategy.md` — 대응 전략서
- `05_decision_document.md` — 통합 의사결정 문서
- `06_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/decision-trigger-mapper/SKILL.md`
- `.agents/skills/scenario-narrative-engine/SKILL.md`
- `.agents/skills/steep-framework/SKILL.md`
