---
name: proposal-writer
description: >-
  Trigger when: 사용자가 `proposal-writer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Proposal Writer Harness

제안서의 고객분석→솔루션설계→가격→차별화→디자인을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `client-analyst`: 제안서 고객 분석가. 잠재 고객의 비즈니스 현황, 과제, 의사결정 구조, 경쟁 상황을 분석하여 제안서의 전략적 방향을 수립한다.
- `differentiator`: 제안서 차별화 전략가. 자사의 고유한 강점(USP), 경쟁우위, 실적/레퍼런스를 활용하여 경쟁 제안 대비 선택받을 수 있는 차별화 전략을 수립한다.
- `pricing-strategist`: 제안서 가격 전략가. 원가 분석, 가격 모델 설계, 경쟁 가격 비교, ROI 산출, 할인/인센티브 전략을 수립한다.
- `proposal-designer`: 제안서 통합 디자이너 및 교차 검증 전문가(QA). 모든 섹션을 통합하여 설득력 있는 최종 제안서를 구성하고, 고객분석-솔루션-가격-차별화 간 정합성을 교차 검증한다.
- `solution-architect`: 제안서 솔루션 설계자. 고객 요구사항에 맞는 기술/서비스 구성을 설계하고, 구현 계획, 일정, 산출물, 품질 보증 방안을 수립한다.

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
- `01_client_analysis.md` — 고객 분석 보고서
- `02_solution_design.md` — 솔루션 설계서
- `03_pricing_model.md` — 가격 전략서
- `04_differentiation.md` — 차별화 전략서
- `05_final_proposal.md` — 최종 제안서 및 검증 보고서

## 확장 스킬

- `.agents/skills/roi-calculator/SKILL.md`
- `.agents/skills/win-theme-builder/SKILL.md`
