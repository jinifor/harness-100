# Newsletter Engine Codex 지침

## 목적

- 이 디렉토리는 `Newsletter Engine` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 둔다.
- 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: [.agents/skills/newsletter-engine/SKILL.md](/Users/hanjin/workspace/repos-jinifor/harness-100/ko/03-newsletter-engine/.agents/skills/newsletter-engine/SKILL.md)
- 전문 agent: `.codex/agents/curator.toml`, `.codex/agents/copywriter.toml`, `.codex/agents/analyst.toml`, `.codex/agents/editor-in-chief.toml`, `.codex/agents/quality-reviewer.toml`
- 확장 스킬: `.agents/skills/email-copywriting/SKILL.md`, `.agents/skills/audience-segmentation/SKILL.md`, `.agents/skills/deliverability-optimization/SKILL.md`

## 실행 원칙

- 전체 작업은 `newsletter-engine` skill로 시작한다.
- 기본 순서는 `curator -> copywriter -> analyst -> editor-in-chief -> quality-reviewer`다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰는 읽기 전용으로 수행하고 findings를 먼저 제시한다.

## 산출물

- `_workspace/00_input.md`
- `_workspace/01_curation_brief.md`
- `_workspace/02_newsletter_draft.md`
- `_workspace/03_ab_test_plan.md`
- `_workspace/04_editorial_final.md`
- `_workspace/05_review_report.md`
