# Code Reviewer Harness Codex 지침

## 목적

- 이 디렉토리는 `Code Reviewer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/code-reviewer/SKILL.md`
- 전문 agent: `.codex/agents/architecture-reviewer.toml`, `.codex/agents/performance-analyst.toml`, `.codex/agents/review-synthesizer.toml`, `.codex/agents/security-analyst.toml`, `.codex/agents/style-inspector.toml`
- 확장 스킬: `.agents/skills/refactoring-catalog/SKILL.md`, `.agents/skills/vulnerability-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `code-reviewer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 코드 리뷰 자동화의 스타일→보안→성능→아키텍처 리뷰를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_style_review.md` — 코드 스타일 리뷰
- `02_security_review.md` — 보안 리뷰
- `03_performance_review.md` — 성능 리뷰
- `04_architecture_review.md` — 아키텍처 리뷰
- `05_review_summary.md` — 종합 리뷰 보고서
