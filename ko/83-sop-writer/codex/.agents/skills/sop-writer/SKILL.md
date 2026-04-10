---
name: sop-writer
description: >-
  Trigger when: 사용자가 `sop-writer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# SOP Writer Harness

표준운영절차(SOP)의 프로세스분석→절차서→체크리스트→교육자료→버전관리를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `checklist-designer`: SOP 체크리스트 설계자. 절차서의 핵심 단계를 실행 점검표로 변환하고, 품질 게이트, 일일/주간/월간 점검 체크리스트를 설계한다.
- `procedure-writer`: SOP 절차서 작성자. 프로세스 분석 결과를 기반으로 누구나 따라할 수 있는 명확한 단계별 절차서를 작성한다. ISO/규제 요건에 부합하는 문서 형식을 적용한다.
- `process-analyst`: SOP 프로세스 분석가. 현행 업무 흐름을 체계적으로 분석하고, 입력/출력/관련자/예외상황을 식별하여 절차서 작성의 기반을 마련한다.
- `training-developer`: SOP 교육자료 제작자. 절차서와 체크리스트를 기반으로 신규 인력이 빠르게 숙달할 수 있는 교육 가이드, 시나리오 연습, 평가 문항을 제작한다.
- `version-controller`: SOP 버전 관리 및 교차 검증 전문가(QA). 절차서-체크리스트-교육자료 간 정합성을 교차 검증하고, 문서 버전 관리 체계를 수립한다.

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
- `01_process_analysis.md` — 프로세스 분석 결과
- `02_procedure_document.md` — 표준 절차서
- `03_checklists.md` — 체크리스트 세트
- `04_training_materials.md` — 교육자료
- `05_version_control.md` — 버전 관리 및 검증 보고서

## 확장 스킬

- `.agents/skills/checklist-design/SKILL.md`
- `.agents/skills/process-mapping/SKILL.md`
