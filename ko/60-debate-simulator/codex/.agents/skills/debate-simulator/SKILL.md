---
name: debate-simulator
description: >-
  Trigger when: 사용자가 `debate-simulator` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Debate Simulator Harness

토론 시뮬레이션 에이전트 팀 하네스.

## Specialist Agents

- `con-debater`: 반대 토론자. 반대 입장의 논거를 체계적으로 구축하고, 찬성 측 논거에 대한 반박을 준비한다.
- `judge`: 토론 심판. 양측의 논증을 공정하게 평가하고, 평가 기준에 따라 승패를 판정하며, 교육적 피드백을 제공한다.
- `pro-debater`: 찬성 토론자. 찬성 입장의 논거를 체계적으로 구축하고, 예상 반론에 대한 반박을 준비한다.
- `rapporteur`: 종합정리자. 토론 전체를 요약하고, 양측 논거를 균형 있게 정리하며, 핵심 시사점을 도출하는 종합 보고서를 작성한다.
- `topic-analyst`: 토론 주제 분석가. 주제의 쟁점을 구조화하고, 핵심 논점을 도출하며, 토론 프레임을 설계한다.

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

- `.agents/skills/argumentation-framework/SKILL.md`
- `.agents/skills/logical-fallacy-detector/SKILL.md`
