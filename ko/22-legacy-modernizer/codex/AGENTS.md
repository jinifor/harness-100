# Legacy Modernizer Harness Codex 지침

## 목적

- 이 디렉토리는 `Legacy Modernizer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/legacy-modernizer/SKILL.md`
- 전문 agent: `.codex/agents/legacy-analyzer.toml`, `.codex/agents/migration-engineer.toml`, `.codex/agents/modernization-reviewer.toml`, `.codex/agents/refactoring-strategist.toml`, `.codex/agents/regression-tester.toml`
- 확장 스킬: `.agents/skills/dependency-analysis/SKILL.md`, `.agents/skills/strangler-fig-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `legacy-modernizer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 레거시 코드베이스를 현대적 아키텍처로 전환하는 에이전트 팀 하네스. 분석→리팩토링전략→마이그레이션→검증 파이프라인을 자동화한다.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_legacy_analysis.md` — 레거시 분석 보고서
- `02_refactoring_strategy.md` — 리팩토링 전략서
- `03_migration_plan.md` — 마이그레이션 실행 계획 및 코드
- `04_test_report.md` — 회귀 테스트 보고서
- `05_review_report.md` — 최종 리뷰 보고서
