# YouTube Production Codex 지침

## 목적

- 이 디렉토리는 `YouTube Production` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: [.agents/skills/youtube-production/SKILL.md](/Users/hanjin/workspace/repos-jinifor/harness-100/ko/01-youtube-production/.agents/skills/youtube-production/SKILL.md)
- 전문 agent: `.codex/agents/content-strategist.toml`, `.codex/agents/scriptwriter.toml`, `.codex/agents/thumbnail-designer.toml`, `.codex/agents/seo-optimizer.toml`, `.codex/agents/production-reviewer.toml`
- 확장 스킬: `.agents/skills/hook-writing/SKILL.md`, `.agents/skills/thumbnail-psychology/SKILL.md`

## 실행 원칙

- 전체 작업은 `youtube-production` skill을 통해 시작한다.
- 작업 순서는 `content-strategist -> scriptwriter/thumbnail-designer(병렬) -> seo-optimizer -> production-reviewer`다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰는 읽기 전용으로 수행하고 findings를 먼저 제시한다.
- 문서에 없는 Codex 키, manifest, asset, script는 만들지 않는다.

## 산출물

- `_workspace/00_input.md`
- `_workspace/01_strategist_brief.md`
- `_workspace/02_scriptwriter_script.md`
- `_workspace/03_thumbnail_concept.md`
- `_workspace/04_seo_package.md`
- `_workspace/05_review_report.md`
- `_workspace/subtitle.srt`
