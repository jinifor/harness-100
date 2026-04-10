---
name: language-tutor
description: >-
  Trigger when: 사용자가 `language-tutor` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Language Tutor Harness

외국어 학습을 위한 레벨 테스트, 커리큘럼, 레슨, 퀴즈, 복습 관리 에이전트 팀 하네스.

## Specialist Agents

- `curriculum-designer`: 외국어 커리큘럼 설계 전문가. 레벨 평가 결과를 기반으로 학습 목표, 단계별 학습 계획, 교재 선정, 마일스톤을 포함한 맞춤 커리큘럼을 설계한다.
- `lesson-tutor`: 외국어 레슨 전문 튜터. 커리큘럼에 따라 문법 설명, 어휘 학습, 회화 연습, 읽기·쓰기 과제를 포함한 구체적 레슨 자료를 생성한다.
- `level-assessor`: 외국어 레벨 평가 전문가. CEFR 기반 진단 테스트를 설계·실시하여 학습자의 현재 수준을 정밀 평가하고, 영역별 강약점을 분석한다.
- `quiz-master`: 외국어 퀴즈 출제 전문가. 학습 내용을 기반으로 다양한 유형의 퀴즈를 출제하고, 난이도를 조절하며, 정확한 채점 기준과 피드백을 제공한다.
- `review-coach`: 복습 코치. 에빙하우스 망각 곡선 기반의 간격 반복 학습을 설계하고, 약점 보강 계획을 수립하며, 전체 학습 진도를 관리한다.

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

## 확장 스킬

- `.agents/skills/cefr-assessment/SKILL.md`
- `.agents/skills/spaced-repetition/SKILL.md`
