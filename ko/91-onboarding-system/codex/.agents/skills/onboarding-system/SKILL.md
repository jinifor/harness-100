---
name: onboarding-system
description: >-
  Trigger when: 사용자가 `onboarding-system` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Onboarding System Harness

신규입사자 온보딩: 체크리스트→교육→멘토배정→30-60-90일 계획까지 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `experience-reviewer`: 온보딩 경험 검증자. 전체 프로그램의 정합성을 교차 검증하고, 개선점을 발견하며, 최종 보고서를 작성한다.
- `mentor-matcher`: 멘토·버디 매칭 전문가. 멘토/버디 역할 정의, 매칭 기준, 멘토 가이드, 관계 관리를 설계한다.
- `milestone-tracker`: 30-60-90일 마일스톤 설계자. 단계별 목표, 성과 기준, 피드백 체계, 진행 추적을 설계한다.
- `onboarding-architect`: 온보딩 설계자. 입사 전부터 90일까지의 온보딩 체크리스트, 일정, 마일스톤, 이해관계자 역할을 설계한다.
- `training-builder`: 교육 콘텐츠 빌더. 온보딩 교육 커리큘럼, 학습 자료, 퀴즈, 자기평가를 설계한다.

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
- `01_onboarding_checklist.md` — 온보딩 체크리스트 및 일정
- `02_training_program.md` — 교육 프로그램
- `03_mentor_guide.md` — 멘토·버디 배정 가이드
- `04_30_60_90_plan.md` — 30-60-90일 계획
- `05_review_report.md` — 온보딩 경험 검증 보고서

## 확장 스킬

- `.agents/skills/buddy-program-guide/SKILL.md`
- `.agents/skills/learning-path-design/SKILL.md`
