---
name: ecommerce-launcher
description: >-
  Trigger when: 사용자가 `ecommerce-launcher` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# E-commerce Launcher Harness

이커머스 상품 런칭의 기획→상세페이지→가격전략→마케팅→CS 셋업을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `cs-architect`: 이커머스 CS 설계자. FAQ, 응대 매뉴얼, 반품/교환 정책, VOC 수집 체계, 에스컬레이션 프로세스를 설계하여 런칭 전 CS 인프라를 완성한다.
- `detail-page-writer`: 이커머스 상세페이지 작성자. 상품 기획서를 기반으로 구매 전환율을 극대화하는 상세페이지 원고를 작성한다. 헤드카피, 상세 구성, SEO, 구매 설득 로직을 포함한다.
- `marketing-manager`: 이커머스 마케팅 매니저. 런칭 캠페인 설계, 채널별 광고 전략, 콘텐츠 마케팅, 인플루언서 협업, 퍼포먼스 마케팅 KPI를 수립한다.
- `pricing-strategist`: 이커머스 가격 전략가. 원가분석, 경쟁가격 조사, 마진 설계, 프로모션 가격, 번들 전략을 수립하여 수익성과 경쟁력을 동시에 확보한다.
- `product-planner`: 이커머스 상품 기획자. 시장조사, 타깃 고객 분석, 경쟁 벤치마킹, 상품 포지셔닝, USP 도출을 수행한다.

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
- `01_product_brief.md` — 상품 기획서
- `02_detail_page.md` — 상세페이지 원고
- `03_pricing_plan.md` — 가격 전략서
- `04_marketing_plan.md` — 마케팅 플랜
- `05_cs_manual.md` — CS 운영 매뉴얼
- `06_review_report.md` — 통합 리뷰 보고서

## 확장 스킬

- `.agents/skills/conversion-optimization/SKILL.md`
- `.agents/skills/product-copy-formulas/SKILL.md`
