---
name: audit-report
description: >-
  Trigger when: 사용자가 `audit-report` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Audit Report Harness

내부감사 보고서 생성 하네스. 감사 범위 설정부터 체크리스트 작성, 발견사항 정리, 개선 권고, 추적 대장까지 에이전트 팀이 협업하여 생성한다.

## Specialist Agents

- `checklist-builder`: 감사 체크리스트 작성 전문가. 감사 기준을 구체적인 통제항목, 테스트 절차, 증빙 요구사항으로 분해하여 현장에서 바로 사용할 수 있는 체크리스트를 작성한다.
- `findings-analyst`: 감사 발견사항 분석 전문가. 체크리스트 결과를 기반으로 발견사항을 구조화하고, 위험 등급을 부여하며, 근본 원인 분석과 영향 평가를 수행한다.
- `recommendation-writer`: 개선 권고 작성 전문가. 발견사항별 시정조치를 설계하고, 이행 계획, 기대 효과, 우선순위를 포함한 실행 가능한 개선 권고안을 작성한다.
- `scope-designer`: 감사 범위 설계 전문가. 감사 목표, 적용 기준(법규/규정/내규), 감사 대상, 감사 기간, 자원 배분을 정의하고 감사 계획서를 작성한다.
- `tracking-manager`: 이행 추적 대장 관리 전문가. 감사 발견사항의 시정조치 이행 현황을 추적하고, 후속 조치, 종결 기준, 에스컬레이션 절차를 관리한다.

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

- `00_input.md` — 감사 요청 및 배경 정리
- `01_audit_scope.md` — 감사 범위 및 계획
- `02_audit_checklist.md` — 감사 체크리스트
- `03_audit_findings.md` — 발견사항 보고서
- `04_recommendations.md` — 개선 권고안
- `05_tracking_ledger.md` — 이행 추적 대장
- `06_final_report.md` — 종합 감사 보고서

## 확장 스킬

- `.agents/skills/finding-classification/SKILL.md`
- `.agents/skills/internal-control-framework/SKILL.md`
