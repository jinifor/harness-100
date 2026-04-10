# Chatbot Builder Harness Codex 지침

## 목적

- 이 디렉토리는 `Chatbot Builder Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/chatbot-builder/SKILL.md`
- 전문 agent: `.codex/agents/conversation-designer.toml`, `.codex/agents/dialog-tester.toml`, `.codex/agents/integration-engineer.toml`, `.codex/agents/nlu-developer.toml`, `.codex/agents/persona-architect.toml`
- 확장 스킬: `.agents/skills/conversation-flow-validator/SKILL.md`, `.agents/skills/intent-taxonomy-builder/SKILL.md`

## 실행 원칙

- 전체 작업은 `chatbot-builder` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 챗봇 구축의 의도분석→대화설계→NLU→통합→테스트를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_persona_spec.md` — 봇 페르소나 명세
- `02_conversation_design.md` — 대화 설계서
- `03_nlu_config.md` — NLU 설정 및 학습 데이터
- `04_integration_spec.md` — 통합 명세서
- `05_test_report.md` — 테스트 보고서
- `src/` — 챗봇 소스코드
