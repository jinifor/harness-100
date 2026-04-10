# Comic Creator Harness Codex 지침

## 목적

- 이 디렉토리는 `Comic Creator Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/comic-creator/SKILL.md`
- 전문 agent: `.codex/agents/comic-editor.toml`, `.codex/agents/dialogue-writer.toml`, `.codex/agents/image-generator.toml`, `.codex/agents/quality-reviewer.toml`, `.codex/agents/storyboarder.toml`
- 확장 스킬: `.agents/skills/character-design-system/SKILL.md`, `.agents/skills/panel-composition/SKILL.md`, `.agents/skills/visual-narrative/SKILL.md`

## 실행 원칙

- 전체 작업은 `comic-creator` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 4컷/장편 만화 제작의 콘티→대사→이미지생성→편집을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_storyboard.md` — 콘티/스토리보드
- `02_dialogue.md` — 대사 스크립트
- `03_image_prompts.md` — 이미지 생성 프롬프트 및 결과
- `04_layout.md` — 페이지 레이아웃/편집 지시서
- `05_review_report.md` — 리뷰 보고서
- `panels/` — 생성된 패널 이미지
