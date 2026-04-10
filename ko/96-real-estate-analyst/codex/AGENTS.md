# Real Estate Analyst Harness Codex 지침

## 목적

- 이 디렉토리는 `Real Estate Analyst Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/real-estate-analyst/SKILL.md`
- 전문 agent: `.codex/agents/location-analyst.toml`, `.codex/agents/market-researcher.toml`, `.codex/agents/profitability-analyst.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/risk-assessor.toml`
- 확장 스킬: `.agents/skills/cap-rate-calculator/SKILL.md`, `.agents/skills/location-scoring/SKILL.md`

## 실행 원칙

- 전체 작업은 `real-estate-analyst` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 부동산 분석 하네스. 시장조사, 입지분석, 수익성 분석, 리스크 평가, 투자 보고서까지 에이전트 팀이 협업하여 생성한다.

## 산출물

- `00_input.md` — 분석 대상 및 투자 조건 정리
- `01_market_research.md` — 시장조사 보고서
- `02_location_analysis.md` — 입지분석 보고서
- `03_profitability_analysis.md` — 수익성 분석 보고서
- `04_risk_assessment.md` — 리스크 평가 보고서
- `05_investment_report.md` — 종합 투자 보고서
