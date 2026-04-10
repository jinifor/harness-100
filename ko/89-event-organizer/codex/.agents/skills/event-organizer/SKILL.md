---
name: event-organizer
description: >-
  Trigger when: 사용자가 `event-organizer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Event Organizer Harness

이벤트 기획·운영: 컨셉→장소→프로그램→홍보→실행→사후평가까지 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `concept-planner`: 이벤트 컨셉 기획자. 행사 목표, 테마, 타깃 참석자, 예산 프레임워크, 핵심 성공 지표를 설계한다.
- `evaluation-analyst`: 사후 평가 분석가. KPI 측정, 참석자 설문, ROI 분석, 교훈 도출, 사후 보고서를 작성한다.
- `logistics-manager`: 로지스틱스 매니저. 장소 선정, 공간 배치, 동선 설계, 장비/기술, 케이터링, 안전 관리를 담당한다.
- `program-designer`: 프로그램 디자이너. 행사 타임테이블, 세션 구성, 연사 관리, 참여형 콘텐츠를 설계한다.
- `promotion-lead`: 홍보 담당. 채널별 홍보 전략, 콘텐츠 제작, 등록 관리, 참석자 커뮤니케이션을 담당한다.

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
- `01_concept_plan.md` — 컨셉 기획서
- `02_logistics_plan.md` — 로지스틱스 계획서
- `03_program_design.md` — 프로그램 설계서
- `04_promotion_plan.md` — 홍보 계획서
- `05_evaluation_framework.md` — 평가 프레임워크

## 확장 스킬

- `.agents/skills/budget-planning/SKILL.md`
- `.agents/skills/venue-evaluation/SKILL.md`
