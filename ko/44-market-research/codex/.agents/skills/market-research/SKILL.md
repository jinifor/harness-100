---
name: market-research
description: >-
  Trigger when: 사용자가 `market-research` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Market Research Harness

시장 조사의 산업분석→경쟁분석→소비자조사→트렌드→보고서를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `competitor-analyst`: 경쟁 분석가. 경쟁사 매핑, 전략 그룹 분석, SWOT 분석, 포지셔닝 맵 작성, 경쟁 우위 도출을 수행한다.
- `consumer-analyst`: 소비자 분석가. 고객 세그먼테이션, 구매 여정 매핑, 니즈 분석, 페르소나 설계, 조사 방법론 제안을 수행한다.
- `industry-analyst`: 산업 분석가. 시장 규모·성장률 산정, 밸류체인 분석, 산업 구조(Porter's 5 Forces), 규제 환경 분석을 수행한다.
- `research-reviewer`: 리서치 검증자(QA). 산업-경쟁-소비자-트렌드 분석 간의 일관성을 교차 검증하고, 인사이트를 통합하여 전략적 권고를 도출한다.
- `trend-analyst`: 트렌드 분석가. 거시 환경(PESTLE), 미시 트렌드, 기술 트렌드, 시나리오 분석, 미래 전망을 수행한다.

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
- `01_industry_analysis.md` — 산업 분석 보고서
- `02_competitor_analysis.md` — 경쟁 분석 보고서
- `03_consumer_analysis.md` — 소비자 분석 보고서
- `04_trend_analysis.md` — 트렌드 분석 보고서
- `05_review_report.md` — 종합 리서치 보고서

## 확장 스킬

- `.agents/skills/porter-five-forces/SKILL.md`
- `.agents/skills/tam-sam-som-calculator/SKILL.md`
