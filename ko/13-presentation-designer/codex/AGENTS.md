# Presentation Designer Harness Codex 지침

## 목적

- 이 디렉토리는 `Presentation Designer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/presentation-designer/SKILL.md`
- 전문 agent: `.codex/agents/deck-reviewer.toml`, `.codex/agents/info-architect.toml`, `.codex/agents/presentation-coach.toml`, `.codex/agents/storyteller.toml`, `.codex/agents/visual-designer.toml`
- 확장 스킬: `.agents/skills/data-visualization-guide/SKILL.md`, `.agents/skills/slide-layout-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `presentation-designer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 프레젠테이션의 기획→스토리보드→슬라이드→발표노트를 에이전트 팀이 협업하여 제작하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_story_structure.md` — 스토리 구조·메시지 맵
- `02_info_design.md` — 정보 설계·데이터 시각화 가이드
- `03_slide_deck.md` — 슬라이드 덱 (마크다운 기반)
- `04_speaker_notes.md` — 발표 노트·타이밍·Q&A
- `05_review_report.md` — 리뷰 보고서
