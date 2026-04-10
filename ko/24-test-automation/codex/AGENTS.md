# Test Automation Harness Codex 지침

## 목적

- 이 디렉토리는 `Test Automation Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/test-automation/SKILL.md`
- 전문 agent: `.codex/agents/coverage-analyst.toml`, `.codex/agents/integration-tester.toml`, `.codex/agents/qa-reviewer.toml`, `.codex/agents/test-strategist.toml`, `.codex/agents/unit-tester.toml`
- 확장 스킬: `.agents/skills/mocking-strategy/SKILL.md`, `.agents/skills/test-design-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `test-automation` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 테스트 자동화 전략 수립부터 테스트 작성, CI 통합, 커버리지 분석까지 에이전트 팀이 협업하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_test_strategy.md` — 테스트 전략서
- `02_unit_tests.md` — 단위 테스트 코드 및 가이드
- `03_integration_tests.md` — 통합 테스트 코드 및 가이드
- `04_coverage_report.md` — 커버리지 분석 보고서
- `05_review_report.md` — 최종 리뷰 보고서
