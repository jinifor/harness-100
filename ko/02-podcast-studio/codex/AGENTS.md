# Podcast Studio Codex 지침

## 목적

- 이 디렉토리는 `Podcast Studio` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 둔다.
- 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: [.agents/skills/podcast-studio/SKILL.md](/Users/hanjin/workspace/repos-jinifor/harness-100/ko/02-podcast-studio/.agents/skills/podcast-studio/SKILL.md)
- 전문 agent: `.codex/agents/researcher.toml`, `.codex/agents/scriptwriter.toml`, `.codex/agents/shownote-editor.toml`, `.codex/agents/distribution-manager.toml`, `.codex/agents/production-reviewer.toml`
- 확장 스킬: `.agents/skills/interview-techniques/SKILL.md`, `.agents/skills/audio-storytelling/SKILL.md`, `.agents/skills/podcast-growth/SKILL.md`

## 실행 원칙

- 전체 작업은 `podcast-studio` skill로 시작한다.
- 기본 순서는 `researcher -> scriptwriter -> shownote-editor/distribution-manager(병렬) -> production-reviewer`다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰는 읽기 전용으로 수행하고 findings를 먼저 제시한다.

## 산출물

- `_workspace/00_input.md`
- `_workspace/01_research_brief.md`
- `_workspace/02_script.md`
- `_workspace/03_shownotes.md`
- `_workspace/04_distribution_package.md`
- `_workspace/05_review_report.md`
