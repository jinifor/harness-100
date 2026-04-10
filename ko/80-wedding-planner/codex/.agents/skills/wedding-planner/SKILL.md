---
name: wedding-planner
description: >-
  Trigger when: 사용자가 `wedding-planner` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Wedding Planner Harness

결혼 준비 종합의 타임라인설계→예산관리표→업체비교표→체크리스트→청첩장문구를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `budget-controller`: 예산 관리자. 결혼 준비 전체 예산을 항목별로 배분하고, 지출 추적 템플릿과 비용 절감 전략을 제공한다.
- `checklist-builder`: 체크리스트 빌더. 결혼 준비 전체 체크리스트를 카테고리별로 작성하고, 맞춤형 청첩장 문구를 제안한다.
- `timeline-designer`: 타임라인 설계자. 결혼식 D-day를 기준으로 역산하여 월별·주별 준비 일정을 설계하고, 핵심 마일스톤을 정의한다.
- `vendor-analyst`: 업체 비교 분석가. 웨딩홀, 스드메, 허니문 등 주요 업체를 조사하고 비교표를 작성하며 선택 가이드를 제공한다.
- `wedding-reviewer`: 웨딩 리뷰어(QA). 타임라인-예산-업체-체크리스트 간의 일관성을 교차 검증하고, 누락·충돌·비현실적 항목을 발견하여 피드백한다.

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
- `01_timeline.md` — 결혼 준비 타임라인
- `02_budget.md` — 예산 관리표
- `03_vendor_comparison.md` — 업체 비교표
- `04_checklist_invitation.md` — 체크리스트 + 청첩장 문구
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/vendor-negotiation-guide/SKILL.md`
- `.agents/skills/wedding-budget-optimizer/SKILL.md`
