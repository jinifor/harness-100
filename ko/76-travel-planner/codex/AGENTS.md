# Travel Planner Harness Codex 지침

## 목적

- 이 디렉토리는 `Travel Planner Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/travel-planner/SKILL.md`
- 전문 agent: `.codex/agents/budget-manager.toml`, `.codex/agents/destination-analyst.toml`, `.codex/agents/itinerary-designer.toml`, `.codex/agents/local-guide.toml`
- 확장 스킬: `.agents/skills/budget-calculator/SKILL.md`, `.agents/skills/route-optimizer/SKILL.md`

## 실행 원칙

- 전체 작업은 `travel-planner` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 여행 계획의 목적지분석→일정→숙소→예산→현지정보를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_destination_analysis.md` — 목적지 분석 보고서
- `02_itinerary.md` — 일정표
- `03_accommodation.md` — 숙소 가이드
- `04_budget.md` — 예산 계획서
- `05_local_guide.md` — 현지 정보 가이드
