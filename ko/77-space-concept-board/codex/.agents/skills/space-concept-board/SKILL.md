---
name: space-concept-board
description: >-
  Trigger when: 사용자가 `space-concept-board` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Space Concept Board Harness

공간 인테리어 컨셉보드의 스타일분석→무드보드→컬러팔레트→가구·소품리스트→예산표→쇼핑가이드를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `budget-manager`: 예산 관리자. 아이템 리스트를 기반으로 예산표를 작성하고, 우선순위별 구매 전략과 쇼핑가이드를 제공한다.
- `concept-reviewer`: 컨셉 리뷰어(QA). 스타일분석-무드보드-아이템리스트-예산표 간의 일관성을 교차 검증하고, 실용성·심미성·예산 정합성을 종합 평가한다.
- `item-curator`: 아이템 큐레이터. 무드보드와 스타일에 맞는 가구·소품을 선정하고, 공간 배치를 제안하며, 구매처와 대안 제품을 조사한다.
- `moodboard-designer`: 무드보드 설계자. 스타일 분석 결과를 바탕으로 컬러팔레트, 텍스처·소재 보드, 공간 분위기를 시각적으로 구성한다.
- `style-analyst`: 공간 스타일 분석가. 사용자의 공간 조건, 라이프스타일, 취향을 분석하여 최적 인테리어 스타일을 진단하고, 레퍼런스 이미지와 사례를 수집한다.

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
- `01_style_analysis.md` — 스타일 분석 보고서
- `02_moodboard.md` — 무드보드 + 컬러팔레트
- `03_item_list.md` — 가구·소품 리스트 + 배치 제안
- `04_budget_shopping.md` — 예산표 + 쇼핑가이드
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/color-harmony-engine/SKILL.md`
- `.agents/skills/spatial-layout-guide/SKILL.md`
