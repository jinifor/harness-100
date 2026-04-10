# Product Manager Harness Codex 지침

## 목적

- 이 디렉토리는 `Product Manager Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/product-manager/SKILL.md`
- 전문 agent: `.codex/agents/pm-reviewer.toml`, `.codex/agents/prd-writer.toml`, `.codex/agents/sprint-planner.toml`, `.codex/agents/story-writer.toml`, `.codex/agents/strategist.toml`
- 확장 스킬: `.agents/skills/rice-prioritizer/SKILL.md`, `.agents/skills/story-point-estimator/SKILL.md`

## 실행 원칙

- 전체 작업은 `product-manager` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- PM 업무의 로드맵→PRD→유저스토리→스프린트→회고를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_product_roadmap.md` — 제품 로드맵
- `02_prd.md` — 제품 요구사항 정의서
- `03_user_stories.md` — 유저스토리 목록
- `04_sprint_plan.md` — 스프린트 계획
- `05_review_report.md` — PM 검증 보고서
