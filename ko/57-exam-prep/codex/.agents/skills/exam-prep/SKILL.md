---
name: exam-prep
description: >-
  Trigger when: 사용자가 `exam-prep` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Exam Prep Harness

시험 준비의 출제경향→약점진단→맞춤학습→모의고사→오답분석 에이전트 팀 하네스.

## Specialist Agents

- `diagnostician`: 약점 진단 전문가. 학습자의 현재 실력 수준을 영역별로 측정하고, 취약점을 식별하여 맞춤형 학습 전략의 기반을 제공한다.
- `error-analyst`: 오답 분석가. 모의고사 결과를 분석하여 오답 패턴을 파악하고, 개념 결손을 진단하며, 맞춤형 보완 전략을 수립한다.
- `examiner`: 모의고사 출제자. 실전과 동일한 형식·난이도·시간의 모의고사를 출제하고, 상세한 해설을 작성한다.
- `learning-designer`: 맞춤학습 설계자. 약점 진단 결과를 기반으로 개인화된 학습 커리큘럼, 일정, 학습자료를 설계한다.
- `trend-analyst`: 시험 출제경향 분석가. 기출문제 패턴 분석, 빈출 영역 도출, 난이도 추이 파악, 출제 예상 영역 예측을 수행한다.

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

- `.agents/skills/bloom-taxonomy-engine/SKILL.md`
- `.agents/skills/error-pattern-analyzer/SKILL.md`
