---
name: gov-funding-plan
description: >-
  Trigger when: 사용자가 `gov-funding-plan` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Gov Funding Plan Harness

정부지원사업 사업계획서의 공고요건분석→기술성·사업성작성→예산편성→증빙준비→제출검증을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `announcement-analyst`: 공고 분석가. 정부지원사업 공고문의 지원 요건, 평가 기준, 배점 비중, 우대 사항, 제출 서류를 체계적으로 분석한다.
- `biz-writer`: 사업성 작성자. 시장 분석, 사업화 전략, 마케팅 계획, 기대효과, 활용 방안을 정부 사업계획서 양식에 맞게 작성한다.
- `budget-planner`: 예산 편성자. 정부 R&D 예산 기준에 맞는 비목별 편성, 인건비 계산, 간접비 산정, 민간부담금 배분, 증빙 가이드를 수행한다.
- `submission-reviewer`: 제출 검증자(QA). 공고요건-기술성-사업성-예산 간의 정합성, 누락 항목, 감점 요인을 교차 검증하고, 제출 준비 상태를 평가한다.
- `tech-writer`: 기술성 작성자. 기술 개발 목표, 개발 내용, 기술 차별성, 연구 방법론, 추진 체계를 정부 사업계획서 양식에 맞게 작성한다.

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
- `01_announcement_analysis.md` — 공고 요건 분석서
- `02_tech_proposal.md` — 기술성 파트
- `03_biz_proposal.md` — 사업성 파트
- `04_budget_plan.md` — 예산 편성서
- `05_review_report.md` — 제출 검증 보고서

## 확장 스킬

- `.agents/skills/budget-standard-checker/SKILL.md`
- `.agents/skills/scoring-optimizer/SKILL.md`
