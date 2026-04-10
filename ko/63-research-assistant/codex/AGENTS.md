# Research Assistant Harness Codex 지침

## 목적

- 이 디렉토리는 `Research Assistant Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/research-assistant/SKILL.md`
- 전문 agent: `.codex/agents/critic-synthesizer.toml`, `.codex/agents/literature-searcher.toml`, `.codex/agents/note-taker.toml`, `.codex/agents/reference-manager.toml`, `.codex/agents/research-coordinator.toml`
- 확장 스킬: `.agents/skills/citation-formatter/SKILL.md`, `.agents/skills/systematic-review-protocol/SKILL.md`

## 실행 원칙

- 전체 작업은 `research-assistant` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 학술 연구 보조 에이전트 팀 하네스.
