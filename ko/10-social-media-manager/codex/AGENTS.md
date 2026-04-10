# Social Media Manager Harness Codex 지침

## 목적

- 이 디렉토리는 `Social Media Manager Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/social-media-manager/SKILL.md`
- 전문 agent: `.codex/agents/copywriter.toml`, `.codex/agents/hashtag-analyst.toml`, `.codex/agents/performance-reviewer.toml`, `.codex/agents/sns-strategist.toml`, `.codex/agents/visual-planner.toml`
- 확장 스킬: `.agents/skills/hashtag-science/SKILL.md`, `.agents/skills/platform-algorithms/SKILL.md`, `.agents/skills/viral-copywriting/SKILL.md`

## 실행 원칙

- 전체 작업은 `social-media-manager` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- SNS 콘텐츠 달력·포스트작성·해시태그·성과분석을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_strategy.md` — SNS 전략/콘텐츠 달력
- `02_posts.md` — 포스트 카피 모음
- `03_visuals.md` — 비주얼 기획서
- `04_hashtags.md` — 해시태그 전략서
- `05_review_report.md` — 리뷰 보고서
