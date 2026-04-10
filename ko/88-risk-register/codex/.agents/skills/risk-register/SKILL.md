---
name: risk-register
description: >-
  Trigger when: 사용자가 `risk-register` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Risk Register Harness

프로젝트 리스크 관리대장: 리스크식별→확률·영향평가→대응전략수립→모니터링계획→상태보고서까지 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `assessment-analyst`: 리스크 평가 분석가. 확률·영향 매트릭스, 기대금전가치(EMV), 리스크 점수 산정, 우선순위 결정을 수행한다.
- `monitoring-planner`: 리스크 모니터링 설계자. KRI(핵심리스크지표), 트리거 조건, 모니터링 주기, 리뷰 프로세스를 설계한다.
- `report-writer`: 리스크 상태 보고서 작성자. 경영진용 대시보드, 트렌드 분석, 리스크 히트맵을 포함한 종합 리스크 보고서를 작성한다.
- `response-strategist`: 리스크 대응 전략가. 리스크별 최적 대응 전략(회피/전가/완화/수용)을 수립하고, 대응 계획과 잔여 리스크를 관리한다.
- `risk-identifier`: 리스크 식별 전문가. 프로젝트 특성에 맞는 체계적 리스크 식별, RBS(Risk Breakdown Structure) 작성, 리스크 카테고리별 도출을 수행한다.

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
- `01_risk_identification.md` — 리스크 식별 보고서
- `02_risk_assessment.md` — 확률·영향 평가 매트릭스
- `03_response_strategy.md` — 대응 전략 계획서
- `04_monitoring_plan.md` — 모니터링 계획
- `05_status_report.md` — 리스크 상태 보고서

## 확장 스킬

- `.agents/skills/risk-response-patterns/SKILL.md`
- `.agents/skills/risk-scoring-matrix/SKILL.md`
