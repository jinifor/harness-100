# Crisis Communication Harness Codex 지침

## 목적

- 이 디렉토리는 `Crisis Communication Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/crisis-communication/SKILL.md`
- 전문 agent: `.codex/agents/media-monitor.toml`, `.codex/agents/message-strategist.toml`, `.codex/agents/press-release-writer.toml`, `.codex/agents/qa-preparer.toml`, `.codex/agents/situation-analyst.toml`
- 확장 스킬: `.agents/skills/media-response-templates/SKILL.md`, `.agents/skills/stakeholder-mapping/SKILL.md`

## 실행 원칙

- 전체 작업은 `crisis-communication` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 위기 상황 발생 시 상황파악→메시지전략→보도자료→Q&A→모니터링까지 에이전트 팀이 협업하여 통합 위기소통 패키지를 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_situation_analysis.md` — 상황 분석 보고서
- `02_message_strategy.md` — 메시지 전략서
- `03_press_release.md` — 보도자료/공식 입장문
- `04_qa_briefing.md` — Q&A 브리핑 시트
- `05_monitoring_plan.md` — 모니터링 계획 및 후속 대응 가이드
