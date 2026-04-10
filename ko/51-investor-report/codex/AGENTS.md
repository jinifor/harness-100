# Investor Report Harness Codex 지침

## 목적

- 이 디렉토리는 `Investor Report Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/investor-report/SKILL.md`
- 전문 agent: `.codex/agents/financial-analyst.toml`, `.codex/agents/ir-reviewer.toml`, `.codex/agents/kpi-designer.toml`, `.codex/agents/market-analyst.toml`, `.codex/agents/strategy-updater.toml`
- 확장 스킬: `.agents/skills/financial-ratio-analyzer/SKILL.md`, `.agents/skills/ir-narrative-builder/SKILL.md`, `.agents/skills/kpi-benchmark-engine/SKILL.md`

## 실행 원칙

- 전체 작업은 `investor-report` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 투자자 보고서 생성: 재무실적분석→KPI대시보드→시장동향→전략업데이트→리스크공시를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_financial_analysis.md` — 재무 실적 분석서
- `02_kpi_dashboard.md` — KPI 대시보드
- `03_market_trends.md` — 시장 동향 보고서
- `04_strategy_update.md` — 전략 업데이트 및 리스크 공시
- `05_review_report.md` — 리뷰 보고서
- `06_investor_report_final.md` — 최종 통합 보고서
