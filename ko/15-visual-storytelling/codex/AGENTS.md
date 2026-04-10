# Visual Storytelling Harness Codex 지침

## 목적

- 이 디렉토리는 `Visual Storytelling Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/visual-storytelling/SKILL.md`
- 전문 agent: `.codex/agents/editorial-reviewer.toml`, `.codex/agents/essay-writer.toml`, `.codex/agents/image-prompter.toml`, `.codex/agents/layout-builder.toml`, `.codex/agents/story-architect.toml`
- 확장 스킬: `.agents/skills/image-prompt-engineering/SKILL.md`, `.agents/skills/narrative-structure-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `visual-storytelling` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 비주얼 스토리텔링의 스토리설계→텍스트집필→AI이미지생성→HTML레이아웃→통합편집을 에이전트 팀이 협업하여 제작하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_story_blueprint.md` — 스토리 블루프린트
- `02_essay_text.md` — 에세이 본문
- `03_image_prompts.md` — 이미지 프롬프트 시트
- `04_layout.html` — HTML 레이아웃
- `05_review_report.md` — 편집 리뷰 보고서
- `images/` — 생성된 이미지 디렉토리
