# Pricing Strategy Harness Codex 지침

## 목적

- 이 디렉토리는 `Pricing Strategy Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/pricing-strategy/SKILL.md`
- 전문 agent: `.codex/agents/competitive-analyst.toml`, `.codex/agents/cost-analyst.toml`, `.codex/agents/pricing-reviewer.toml`, `.codex/agents/pricing-simulator.toml`, `.codex/agents/value-assessor.toml`
- 확장 스킬: `.agents/skills/price-elasticity-calculator/SKILL.md`, `.agents/skills/psm-analyzer/SKILL.md`

## 실행 원칙

- 전체 작업은 `pricing-strategy` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 가격 전략 수립: 원가분석→경쟁가격→가치기반→시뮬레이션을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_cost_analysis.md` — 원가 분석서
- `02_competitive_pricing.md` — 경쟁 가격 분석서
- `03_value_pricing.md` — 가치 기반 가격 분석서
- `04_pricing_simulation.md` — 가격 시뮬레이션 보고서
- `05_review_report.md` — 리뷰 보고서
