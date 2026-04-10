# Tax Calculator Harness Codex 지침

## 목적

- 이 디렉토리는 `Tax Calculator Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/tax-calculator/SKILL.md`
- 전문 agent: `.codex/agents/deduction-optimizer.toml`, `.codex/agents/income-analyst.toml`, `.codex/agents/strategy-advisor.toml`, `.codex/agents/tax-engine.toml`
- 확장 스킬: `.agents/skills/deduction-optimizer-engine/SKILL.md`, `.agents/skills/tax-bracket-simulator/SKILL.md`

## 실행 원칙

- 전체 작업은 `tax-calculator` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 세금 계산·절세 전략의 소득분석→공제항목최적화→세액계산→절세시뮬레이션→신고자료준비를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_income_analysis.md` — 소득 분석 보고서
- `02_deduction_optimization.md` — 공제 최적화 보고서
- `03_tax_calculation.md` — 세액 계산서
- `04_tax_strategy.md` — 절세 전략 및 시뮬레이션
- `05_filing_preparation.md` — 신고 자료 준비 가이드
