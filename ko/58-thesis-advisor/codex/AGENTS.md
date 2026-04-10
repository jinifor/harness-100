# Thesis Advisor Harness Codex 지침

## 목적

- 이 디렉토리는 `Thesis Advisor Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/thesis-advisor/SKILL.md`
- 전문 agent: `.codex/agents/literature-analyst.toml`, `.codex/agents/methodology-expert.toml`, `.codex/agents/proofreader.toml`, `.codex/agents/topic-explorer.toml`, `.codex/agents/writing-coach.toml`
- 확장 스킬: `.agents/skills/academic-writing-style/SKILL.md`, `.agents/skills/research-methodology/SKILL.md`

## 실행 원칙

- 전체 작업은 `thesis-advisor` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 논문 작성의 주제선정→문헌조사→방법론→집필→교정 에이전트 팀 하네스.
