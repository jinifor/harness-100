# Meal Planner Harness Codex 지침

## 목적

- 이 디렉토리는 `Meal Planner Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/meal-planner/SKILL.md`
- 전문 agent: `.codex/agents/meal-designer.toml`, `.codex/agents/nutritionist.toml`, `.codex/agents/recipe-writer.toml`, `.codex/agents/shopping-coordinator.toml`
- 확장 스킬: `.agents/skills/ingredient-substitution-engine/SKILL.md`, `.agents/skills/nutrition-calculator/SKILL.md`

## 실행 원칙

- 전체 작업은 `meal-planner` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 식단 관리의 영양분석→식단설계→레시피→장보기목록→조리가이드를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_nutrition_analysis.md` — 영양 분석 보고서
- `02_meal_plan.md` — 식단표
- `03_recipes.md` — 레시피 모음
- `04_shopping_list.md` — 장보기 목록
- `05_cooking_guide.md` — 조리 가이드 및 밀프렙 플랜
