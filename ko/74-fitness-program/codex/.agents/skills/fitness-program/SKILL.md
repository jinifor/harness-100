---
name: fitness-program
description: >-
  Trigger when: 사용자가 `fitness-program` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Fitness Program Harness

운동 프로그램의 목표별설계→주간스케줄→운동가이드→식단연계→진행기록을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `exercise-guide`: 운동 가이드 작성자. 프로그램에 포함된 각 운동의 올바른 폼, 호흡법, 흔한 실수, 대체 운동을 상세히 안내한다.
- `nutrition-linker`: 영양 연계 전문가. 운동 프로그램에 맞는 영양 전략을 수립하고, 운동 전후 영양 타이밍·보충제·수분 섭취 가이드를 제공한다.
- `program-architect`: 운동 프로그램 설계자. 사용자의 목표·체력수준·가용시간을 분석하여 주기화된 운동 프로그램을 설계하고, 볼륨·강도·빈도를 최적화한다.
- `template-builder`: 템플릿 빌더. 운동 기록지, 체성분 추적표, 진행 사진 가이드, 주기별 평가 양식 등 프로그램 진행을 추적·관리하는 템플릿을 생성한다.

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
- `01_program_design.md` — 프로그램 설계서
- `02_weekly_schedule.md` — 주간 운동 스케줄
- `03_exercise_guide.md` — 운동 가이드 문서
- `04_nutrition_plan.md` — 식단 연계표
- `05_tracking_template.md` — 진행 기록 템플릿

## 확장 스킬

- `.agents/skills/exercise-biomechanics/SKILL.md`
- `.agents/skills/periodization-engine/SKILL.md`
