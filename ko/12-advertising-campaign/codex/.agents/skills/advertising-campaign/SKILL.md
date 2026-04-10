---
name: advertising-campaign
description: >-
  Trigger when: 사용자가 `advertising-campaign` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Advertising Campaign Harness

광고 캠페인의 타깃분석→카피→크리에이티브→미디어플랜을 에이전트 팀이 협업하여 설계하는 하네스.

## Specialist Agents

- `campaign-reviewer`: 캠페인 리뷰어(QA). 시장분석-카피-크리에이티브-미디어플랜 간의 일관성을 교차 검증하고, 누락·모순·품질 문제를 발견하여 피드백을 제공한다.
- `copywriter`: 광고 카피라이터. 타깃 분석을 기반으로 헤드라인, 바디카피, CTA, 슬로건 등 캠페인 전 채널의 광고 카피를 작성한다.
- `creative-director`: 크리에이티브 디렉터. 광고 캠페인의 비주얼 컨셉을 설계하고, 스토리보드를 작성하며, Gemini 이미지 생성을 활용하여 광고 비주얼 시안을 제작한다.
- `market-analyst`: 광고 캠페인 시장·타깃 분석가. 제품/서비스의 타깃 오디언스를 세분화하고, 경쟁 광고를 분석하며, 캠페인 전략의 토대가 되는 인사이트를 도출한다.
- `media-planner`: 미디어 플래너. 캠페인 목표와 예산에 따라 최적의 미디어 믹스를 설계하고, 채널별 예산 배분, 일정, KPI를 수립한다.

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
- `01_market_analysis.md` — 시장·타깃 분석 보고서
- `02_ad_copy.md` — 광고 카피 세트
- `03_creative_concept.md` — 크리에이티브 컨셉·스토리보드
- `04_media_plan.md` — 미디어 플랜
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/ad-copywriting-formulas/SKILL.md`
- `.agents/skills/media-mix-calculator/SKILL.md`
