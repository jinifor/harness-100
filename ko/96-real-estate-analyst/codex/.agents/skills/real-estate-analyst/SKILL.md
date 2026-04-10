---
name: real-estate-analyst
description: >-
  Trigger when: 사용자가 `real-estate-analyst` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Real Estate Analyst Harness

부동산 분석 하네스. 시장조사, 입지분석, 수익성 분석, 리스크 평가, 투자 보고서까지 에이전트 팀이 협업하여 생성한다.

## Specialist Agents

- `location-analyst`: 입지분석 전문가. 교통 접근성, 학군, 상권, 생활 인프라, 개발 호재, 자연환경 등 입지 요소를 다각도로 분석하여 입지 경쟁력을 평가한다.
- `market-researcher`: 부동산 시장조사 전문가. 거시경제 지표, 지역 부동산 시장 동향, 공급·수요 분석, 가격 추이, 정책 변화를 조사하여 시장 환경을 분석한다.
- `profitability-analyst`: 수익성 분석 전문가. 임대수익률, 시세차익, 현금흐름, 레버리지 효과, IRR, NPV 등 부동산 투자의 재무적 수익성을 정밀 분석한다.
- `report-writer`: 투자 보고서 작성 전문가. 시장조사, 입지분석, 수익성, 리스크 분석 결과를 종합하여 투자 의견, 시나리오별 수익 비교, 최종 투자 판단을 포함한 보고서를 작성한다.
- `risk-assessor`: 부동산 리스크 평가 전문가. 규제 리스크, 시장 리스크, 유동성 리스크, 구조적/물리적 리스크, 법적 리스크를 종합 평가하고 리스크 대응 전략을 수립한다.

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

- `00_input.md` — 분석 대상 및 투자 조건 정리
- `01_market_research.md` — 시장조사 보고서
- `02_location_analysis.md` — 입지분석 보고서
- `03_profitability_analysis.md` — 수익성 분석 보고서
- `04_risk_assessment.md` — 리스크 평가 보고서
- `05_investment_report.md` — 종합 투자 보고서

## 확장 스킬

- `.agents/skills/cap-rate-calculator/SKILL.md`
- `.agents/skills/location-scoring/SKILL.md`
