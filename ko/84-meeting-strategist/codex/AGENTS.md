# Meeting Strategist Harness Codex 지침

## 목적

- 이 디렉토리는 `Meeting Strategist Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/meeting-strategist/SKILL.md`
- 전문 agent: `.codex/agents/agenda-architect.toml`, `.codex/agents/background-researcher.toml`, `.codex/agents/followup-planner.toml`, `.codex/agents/framework-designer.toml`, `.codex/agents/template-builder.toml`
- 확장 스킬: `.agents/skills/decision-frameworks/SKILL.md`, `.agents/skills/facilitation-techniques/SKILL.md`

## 실행 원칙

- 전체 작업은 `meeting-strategist` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 회의 전략 문서의 안건구조설계→배경자료조사→의사결정프레임워크→회의록템플릿→팔로업플랜을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_agenda_design.md` — 안건 구조 설계서
- `02_background_brief.md` — 배경 자료 브리프
- `03_decision_framework.md` — 의사결정 프레임워크
- `04_meeting_templates.md` — 회의록 및 보고 템플릿
- `05_followup_plan.md` — 팔로업 플랜 및 검증 보고서
