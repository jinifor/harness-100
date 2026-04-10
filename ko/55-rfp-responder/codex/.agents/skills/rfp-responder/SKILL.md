---
name: rfp-responder
description: >-
  Trigger when: 사용자가 `rfp-responder` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# RFP Responder Harness

RFI/RFP 응답서 작성을 위한 요구사항 분석, 역량 매칭, 기술 제안, 가격 제안, 차별화 전략까지 에이전트 팀이 협업하는 하네스.

## Specialist Agents

- `capability-matcher`: 역량 매칭 전문가. 요구사항 분석 결과를 기반으로 자사의 수행 실적, 투입 인력, 기술 역량을 RFP 요구사항에 매핑하고, 갭과 보완 전략을 도출한다.
- `pricing-strategist`: 가격 제안 전략가. 원가 산정, 가격 전략, 경쟁 포지셔닝을 고려한 최적의 가격 제안서를 작성한다.
- `proposal-reviewer`: 제안서 리뷰어(QA). 요구사항 분석-역량 매칭-기술 제안-가격 제안 간의 정합성을 교차 검증하고, 차별화 전략의 일관성과 최종 완성도를 점검한다.
- `requirement-analyst`: RFP 요구사항 분석 전문가. RFP/RFI 문서를 정밀 해부하여 필수/선택 요구사항을 분류하고, 평가 기준별 배점과 숨겨진 니즈를 파악한다.
- `technical-proposer`: 기술 제안서 작성 전문가. 요구사항 분석과 역량 매칭을 기반으로, 방법론, 아키텍처, 추진 일정, 품질 관리 계획을 포함한 기술 제안서를 작성한다.

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
- `01_requirement_analysis.md` — 요구사항 분석서
- `02_capability_matrix.md` — 역량 매칭 매트릭스
- `03_technical_proposal.md` — 기술 제안서
- `04_pricing_proposal.md` — 가격 제안서
- `05_differentiation_strategy.md` — 차별화 전략서
- `06_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/pricing-calculator/SKILL.md`
- `.agents/skills/win-theme-builder/SKILL.md`
