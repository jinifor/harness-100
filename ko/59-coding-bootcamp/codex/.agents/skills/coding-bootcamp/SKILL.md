---
name: coding-bootcamp
description: >-
  Trigger when: 사용자가 `coding-bootcamp` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Coding Bootcamp Harness

코딩 교육의 커리큘럼설계→실습과제→코드리뷰→프로젝트→포트폴리오를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `code-reviewer`: 코드 리뷰어. 학습자의 코드를 품질, 가독성, 성능, 패턴 관점에서 리뷰하고 구체적인 개선 방향을 제시한다.
- `curriculum-designer`: 커리큘럼 설계자. 학습자의 수준과 목표에 맞는 단계별 학습 경로, 기술 스택 선정, 주간 일정을 설계한다.
- `exercise-creator`: 실습과제 출제자. 커리큘럼에 맞는 난이도별 코딩 문제, 테스트케이스, 풀이 가이드를 작성한다.
- `mentor`: 개발자 멘토. 실전 프로젝트 설계, 포트폴리오 구성, 기술 면접 준비, 커리어 가이드를 제공한다.

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
- `01_curriculum.md` — 커리큘럼
- `02_exercises/` — 실습과제 디렉토리
- `03_code_review.md` — 코드 리뷰 보고서
- `04_project_spec.md` — 프로젝트 기획서
- `05_portfolio_guide.md` — 포트폴리오 가이드

## 확장 스킬

- `.agents/skills/code-kata-generator/SKILL.md`
- `.agents/skills/tech-interview-prep/SKILL.md`
