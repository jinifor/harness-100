---
name: sales-enablement
description: >-
  Trigger when: 사용자가 `sales-enablement` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Sales Enablement Harness

영업 지원 파이프라인: 고객분석→제안서→프레젠테이션→팔로업을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `customer-analyst`: 고객 분석 전문가. 영업 대상 고객의 사업 현황, 니즈, 의사결정 구조, 예산 규모, 경쟁사 이용 현황을 분석하여 맞춤 영업 전략의 기반을 제공한다.
- `followup-manager`: 영업 팔로업 관리 전문가. 제안 이후의 팔로업 일정, 이메일 템플릿, 이의 대응(Objection Handling), 계약 체결까지의 액션 플랜을 수립한다.
- `presenter`: 영업 프레젠테이션 설계 전문가. 제안서 내용을 설득력 있는 프레젠테이션 스토리라인과 슬라이드 구성으로 변환한다. DMU별 맞춤 메시지를 설계한다.
- `proposal-writer`: 영업 제안서 작성 전문가. 고객 분석 결과를 기반으로 맞춤형 솔루션 제안서를 작성한다. 가치 제안, 솔루션 매칭, ROI 산출, 가격 제안을 포함한다.
- `sales-reviewer`: 영업 지원 리뷰어(QA). 고객분석-제안서-프레젠테이션-팔로업 간의 정합성을 교차 검증하고, 영업 전략의 설득력·일관성·완성도를 평가한다.

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
- `01_customer_analysis.md` — 고객 분석서
- `02_proposal.md` — 제안서
- `03_presentation.md` — 프레젠테이션 구성안
- `04_followup_plan.md` — 팔로업 계획서
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/objection-handler/SKILL.md`
- `.agents/skills/roi-calculator/SKILL.md`
