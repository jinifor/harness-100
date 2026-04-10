# Personal Finance Harness Codex 지침

## 목적

- 이 디렉토리는 `Personal Finance Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/personal-finance/SKILL.md`
- 전문 agent: `.codex/agents/budget-planner.toml`, `.codex/agents/finance-reviewer.toml`, `.codex/agents/financial-analyst.toml`, `.codex/agents/investment-advisor.toml`, `.codex/agents/tax-strategist.toml`
- 확장 스킬: `.agents/skills/compound-interest-simulator/SKILL.md`, `.agents/skills/financial-ratio-analyzer/SKILL.md`

## 실행 원칙

- 전체 작업은 `personal-finance` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 개인 재무관리의 수입지출분석→예산설계→투자전략→절세방안→은퇴설계를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_financial_analysis.md` — 수입지출 분석 + 재무건전성 진단
- `02_budget_plan.md` — 예산 설계 + 저축 계획
- `03_investment_strategy.md` — 투자 전략 + 포트폴리오
- `04_tax_strategy.md` — 절세 방안 + 은퇴 설계
- `05_review_report.md` — 리뷰 보고서
