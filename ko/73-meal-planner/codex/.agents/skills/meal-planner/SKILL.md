---
name: meal-planner
description: >-
  Trigger when: 사용자가 `meal-planner` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Meal Planner Harness

식단 관리의 영양분석→식단설계→레시피→장보기목록→조리가이드를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `meal-designer`: 식단 설계 전문가. 영양 분석 결과를 기반으로 일간·주간 식단표를 설계하고, 끼니별 칼로리·영양소 배분을 최적화한다.
- `nutritionist`: 영양 분석 전문가. 사용자의 신체 정보·건강 목표·식이 제한을 분석하여 일일 영양소 목표와 식단 설계 가이드라인을 수립한다.
- `recipe-writer`: 레시피 작성 전문가. 식단표의 각 메뉴에 대한 상세 레시피를 작성하고, 영양정보·조리팁·대체재료를 제공한다.
- `shopping-coordinator`: 장보기·조리 코디네이터. 레시피 재료를 통합하여 장보기 목록을 생성하고, 효율적인 조리 순서와 밀프렙 플랜을 수립한다.

## Workflow

1. 사용자 요청, 제약 조건, 기존 자료를 정리한다.
2. 필요하면 `_workspace/00_input.md`에 시작 컨텍스트를 저장한다.
3. 요청 범위에 맞는 specialist를 순차 또는 병렬로 실행하고, 번호가 매겨진 `_workspace/` 산출물로 handoff 한다.
4. 리뷰어 또는 종합 검토 specialist가 있으면 마지막에 전체 결과를 검증한다.
5. 누락된 단계, 한계, 재사용한 입력 파일을 최종 보고에 명시한다.

## 작업 규칙

- source `.claude` 파일은 수정하지 않는다.
- 모든 하네스 산출물은 `_workspace/`에 유지한다.
- 기존 파일이 이미 있으면 적절한 위치에 복사하거나 참조하고 중복 단계를 건너뛸 수 있다.
- 외부 조회나 생성이 실패해도 가능한 범위까지 진행하고 한계를 적는다.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_nutrition_analysis.md` — 영양 분석 보고서
- `02_meal_plan.md` — 식단표
- `03_recipes.md` — 레시피 모음
- `04_shopping_list.md` — 장보기 목록
- `05_cooking_guide.md` — 조리 가이드 및 밀프렙 플랜

## 확장 스킬

- `.agents/skills/ingredient-substitution-engine/SKILL.md`
- `.agents/skills/nutrition-calculator/SKILL.md`
