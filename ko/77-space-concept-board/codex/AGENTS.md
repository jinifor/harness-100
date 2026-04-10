# Space Concept Board Harness Codex 지침

## 목적

- 이 디렉토리는 `Space Concept Board Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/space-concept-board/SKILL.md`
- 전문 agent: `.codex/agents/budget-manager.toml`, `.codex/agents/concept-reviewer.toml`, `.codex/agents/item-curator.toml`, `.codex/agents/moodboard-designer.toml`, `.codex/agents/style-analyst.toml`
- 확장 스킬: `.agents/skills/color-harmony-engine/SKILL.md`, `.agents/skills/spatial-layout-guide/SKILL.md`

## 실행 원칙

- 전체 작업은 `space-concept-board` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 공간 인테리어 컨셉보드의 스타일분석→무드보드→컬러팔레트→가구·소품리스트→예산표→쇼핑가이드를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_style_analysis.md` — 스타일 분석 보고서
- `02_moodboard.md` — 무드보드 + 컬러팔레트
- `03_item_list.md` — 가구·소품 리스트 + 배치 제안
- `04_budget_shopping.md` — 예산표 + 쇼핑가이드
- `05_review_report.md` — 리뷰 보고서
