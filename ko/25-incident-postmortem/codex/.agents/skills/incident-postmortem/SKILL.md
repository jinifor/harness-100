---
name: incident-postmortem
description: >-
  Trigger when: 사용자가 `incident-postmortem` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Incident Postmortem Harness

장애 사후분석 보고서를 에이전트 팀이 협업하여 생성하는 하네스. 타임라인 재구성→근본원인 분석→영향범위 산정→재발방지 대책→보고서 생성 파이프라인을 자동화한다.

## Specialist Agents

- `impact-assessor`: 영향범위 산정 전문가. 장애의 사용자 영향, 매출 영향, SLA 영향, 평판 영향을 정량적으로 산정하고 비즈니스 임팩트를 종합 평가한다.
- `postmortem-reviewer`: 포스트모텀 리뷰어(QA). 타임라인-근본원인-영향-대책 간의 정합성을 교차 검증하고, 비난 없는 문화가 유지되는지 확인한다.
- `remediation-planner`: 재발방지 대책 수립 전문가. 근본원인과 기여요인에 대한 단기/중기/장기 대책을 수립하고, 오너십과 완료 기한을 명시한 실행 가능한 액션 아이템을 생성한다.
- `root-cause-investigator`: 근본원인 조사 전문가. 5 Whys, 피시본 다이어그램, Fault Tree Analysis를 활용하여 장애의 표면 원인에서 근본 원인까지 추적한다.
- `timeline-reconstructor`: 장애 타임라인 재구성 전문가. 장애 관련 이벤트를 수집하고, 시간순으로 정렬하며, 누락 구간을 식별하여 정확한 장애 경과를 재구성한다.

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
- `01_timeline.md` — 장애 타임라인
- `02_root_cause.md` — 근본원인 분석
- `03_impact_assessment.md` — 영향범위 산정
- `04_remediation_plan.md` — 재발방지 대책
- `05_review_report.md` — 리뷰 보고서
- `postmortem_report.md` — 최종 통합 포스트모텀 보고서

## 확장 스킬

- `.agents/skills/rca-methodology/SKILL.md`
- `.agents/skills/sla-impact-calculator/SKILL.md`
