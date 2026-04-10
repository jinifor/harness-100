---
name: grant-writer
description: >-
  Trigger when: 사용자가 `grant-writer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Grant Writer Harness

보조금 및 지원사업 신청을 위한 공고 분석, 사업계획 작성, 예산 편성, 제출 검증까지 에이전트 팀이 협업하는 하네스.

## Specialist Agents

- `announcement-analyst`: 보조금/지원사업 공고 분석 전문가. 공고문의 자격 요건, 평가 기준, 배점 체계, 핵심 키워드를 분석하여 신청 전략의 기반을 제공한다.
- `budget-designer`: 예산 편성 전문가. 공고 규정에 맞는 비목별 예산을 산정하고, 대응 자금 계획, 집행 계획, 정산 가이드를 작성한다.
- `compliance-checker`: 규정 준수 검증 전문가. 사업계획서와 예산이 공고 요건에 완벽히 부합하는지 검증하고, 배점 최적화를 위한 개선 사항을 도출한다.
- `plan-writer`: 사업계획서 작성 전문가. 공고 분석 결과를 기반으로 평가 기준에 최적화된 사업계획서를 작성한다. 기술성, 사업성, 수행역량을 체계적으로 서술한다.
- `submission-verifier`: 제출 검증 전문가(QA). 신청서 패키지의 완결성을 최종 검증하고, 제출 체크리스트와 제출 가이드를 작성한다.

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
- `01_announcement_analysis.md` — 공고 분석서
- `02_business_plan.md` — 사업계획서
- `03_budget_plan.md` — 예산 편성서
- `04_compliance_report.md` — 규정 준수 보고서
- `05_submission_checklist.md` — 제출 체크리스트
- `06_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/budget-rule-engine/SKILL.md`
- `.agents/skills/scoring-optimizer/SKILL.md`
