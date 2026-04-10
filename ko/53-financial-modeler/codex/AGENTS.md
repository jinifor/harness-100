# Financial Modeler Harness Codex 지침

## 목적

- 이 디렉토리는 `Financial Modeler Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/financial-modeler/SKILL.md`
- 전문 agent: `.codex/agents/cost-analyst.toml`, `.codex/agents/model-reviewer.toml`, `.codex/agents/revenue-modeler.toml`, `.codex/agents/scenario-planner.toml`, `.codex/agents/valuation-expert.toml`
- 확장 스킬: `.agents/skills/dcf-valuation/SKILL.md`, `.agents/skills/sensitivity-analysis/SKILL.md`, `.agents/skills/unit-economics/SKILL.md`

## 실행 원칙

- 전체 작업은 `financial-modeler` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 수익 모델, 비용 구조, 시나리오 분석, 밸류에이션까지 재무 모델링 전 과정을 에이전트 팀이 협업하여 생성하는 하네스.
