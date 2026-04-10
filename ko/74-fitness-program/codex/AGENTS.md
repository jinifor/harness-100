# Fitness Program Harness Codex 지침

## 목적

- 이 디렉토리는 `Fitness Program Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/fitness-program/SKILL.md`
- 전문 agent: `.codex/agents/exercise-guide.toml`, `.codex/agents/nutrition-linker.toml`, `.codex/agents/program-architect.toml`, `.codex/agents/template-builder.toml`
- 확장 스킬: `.agents/skills/exercise-biomechanics/SKILL.md`, `.agents/skills/periodization-engine/SKILL.md`

## 실행 원칙

- 전체 작업은 `fitness-program` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 운동 프로그램의 목표별설계→주간스케줄→운동가이드→식단연계→진행기록을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_program_design.md` — 프로그램 설계서
- `02_weekly_schedule.md` — 주간 운동 스케줄
- `03_exercise_guide.md` — 운동 가이드 문서
- `04_nutrition_plan.md` — 식단 연계표
- `05_tracking_template.md` — 진행 기록 템플릿
