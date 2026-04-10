# Scenario Planner Harness Codex 지침

## 목적

- 이 디렉토리는 `Scenario Planner Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/scenario-planner/SKILL.md`
- 전문 agent: `.codex/agents/impact-assessor.toml`, `.codex/agents/integration-reviewer.toml`, `.codex/agents/scenario-designer.toml`, `.codex/agents/strategy-architect.toml`, `.codex/agents/variable-analyst.toml`
- 확장 스킬: `.agents/skills/decision-trigger-mapper/SKILL.md`, `.agents/skills/scenario-narrative-engine/SKILL.md`, `.agents/skills/steep-framework/SKILL.md`

## 실행 원칙

- 전체 작업은 `scenario-planner` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 불확실한 환경에서 핵심 변수를 정의하고, 시나리오 매트릭스를 구성하여 영향 분석과 대응 전략을 수립하는 에이전트 팀 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_variable_analysis.md` — 핵심 변수 분석서
- `02_scenario_matrix.md` — 시나리오 매트릭스 및 서사
- `03_impact_assessment.md` — 영향 분석 보고서
- `04_response_strategy.md` — 대응 전략서
- `05_decision_document.md` — 통합 의사결정 문서
- `06_review_report.md` — 리뷰 보고서
