---
name: personal-finance
description: >-
  Trigger when: 사용자가 `personal-finance` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Personal Finance Harness

개인 재무관리의 수입지출분석→예산설계→투자전략→절세방안→은퇴설계를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `budget-planner`: 예산 설계자. 재무 분석 결과를 바탕으로 카테고리별 월 예산을 설계하고, 저축 목표와 실천 전략을 수립한다.
- `finance-reviewer`: 재무 리뷰어(QA). 분석-예산-투자-절세 간의 일관성을 교차 검증하고, 수치 정확성, 실행 가능성, 리스크 요인을 종합 평가한다.
- `financial-analyst`: 재무 분석가. 사용자의 수입·지출 구조를 분석하고, 재무 건전성을 진단하며, 개선 포인트를 도출한다.
- `investment-advisor`: 투자 전문가. 사용자의 투자 성향, 목표, 기간에 맞는 자산배분 전략과 포트폴리오를 설계한다.
- `tax-strategist`: 세무 전략가. 소득 구조에 맞는 절세 방안을 수립하고, 세제혜택 극대화 전략과 은퇴 설계를 제공한다.

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
- `01_financial_analysis.md` — 수입지출 분석 + 재무건전성 진단
- `02_budget_plan.md` — 예산 설계 + 저축 계획
- `03_investment_strategy.md` — 투자 전략 + 포트폴리오
- `04_tax_strategy.md` — 절세 방안 + 은퇴 설계
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/compound-interest-simulator/SKILL.md`
- `.agents/skills/financial-ratio-analyzer/SKILL.md`
