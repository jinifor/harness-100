---
name: compliance-checker
description: >-
  Trigger when: 사용자가 `compliance-checker` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Compliance Checker Harness

규정 준수 검증 — 법률매핑→현황진단→갭분석→개선계획을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `gap-analyst`: 갭 분석가. 법적 요구사항과 현재 이행 현황 간의 차이를 분석하고, 리스크를 산정하며, 시정 우선순위를 도출한다.
- `law-mapper`: 규정 준수 법률 분석가. 대상 사업/서비스에 적용되는 법률·규정·표준을 식별하고, 조항별 의무사항을 구조화하여 매핑한다.
- `remediation-planner`: 개선 계획 수립자. 갭 분석 결과를 기반으로 구체적 시정 조치 계획, 일정, 책임자 배정, 모니터링 체계를 설계한다.
- `status-auditor`: 현황 진단자. 조직의 현재 규정 준수 상태를 조사하고, 증거를 수집·분류하며, 의무사항별 이행 현황을 평가한다.

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
- `01_law_mapping.md` — 법률 매핑 보고서
- `02_status_audit.md` — 현황 진단 보고서
- `03_gap_analysis.md` — 갭 분석 보고서
- `04_remediation_plan.md` — 개선 계획서

## 확장 스킬

- `.agents/skills/audit-checklist-engine/SKILL.md`
- `.agents/skills/regulation-knowledge-base/SKILL.md`
