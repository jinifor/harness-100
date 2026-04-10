# Content Repurposer Codex 지침

## 목적

- 이 디렉토리는 `Content Repurposer` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 둔다.
- 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: [.agents/skills/content-repurposer/SKILL.md](/Users/hanjin/workspace/repos-jinifor/harness-100/ko/04-content-repurposer/.agents/skills/content-repurposer/SKILL.md)
- 전문 agent: `.codex/agents/source-analyst.toml`, `.codex/agents/blog-writer.toml`, `.codex/agents/sns-copywriter.toml`, `.codex/agents/presentation-builder.toml`, `.codex/agents/quality-reviewer.toml`
- 확장 스킬: `.agents/skills/platform-adaptation/SKILL.md`, `.agents/skills/content-atomization/SKILL.md`

## 실행 원칙

- 전체 작업은 `content-repurposer` skill로 시작한다.
- 기본 순서는 `source-analyst -> blog-writer/sns-copywriter/presentation-builder(병렬) -> quality-reviewer`다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰는 읽기 전용으로 수행하고 findings를 먼저 제시한다.

## 산출물

- `_workspace/00_input.md`
- `_workspace/01_source_analysis.md`
- `_workspace/02_blog_post.md`
- `_workspace/03_sns_package.md`
- `_workspace/04_presentation.md`
- `_workspace/05_review_report.md`
