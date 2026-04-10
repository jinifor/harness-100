# Game Narrative Harness Codex 지침

## 목적

- 이 디렉토리는 `Game Narrative Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/game-narrative/SKILL.md`
- 전문 agent: `.codex/agents/branch-architect.toml`, `.codex/agents/dialogue-writer.toml`, `.codex/agents/narrative-reviewer.toml`, `.codex/agents/quest-designer.toml`, `.codex/agents/worldbuilder.toml`
- 확장 스킬: `.agents/skills/branching-logic/SKILL.md`, `.agents/skills/dialogue-systems/SKILL.md`, `.agents/skills/quest-design-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `game-narrative` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 게임 스토리·퀘스트·대사·분기 시나리오를 에이전트 팀이 협업하여 설계하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_worldbuilding.md` — 세계관 설정 문서
- `02_quest_design.md` — 퀘스트 설계 문서
- `03_dialogue_script.md` — 대사 스크립트
- `04_branch_map.md` — 분기 구조도
- `05_review_report.md` — 리뷰 보고서
