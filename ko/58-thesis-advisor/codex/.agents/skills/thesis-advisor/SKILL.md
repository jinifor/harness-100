---
name: thesis-advisor
description: >-
  Trigger when: 사용자가 `thesis-advisor` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Thesis Advisor Harness

논문 작성의 주제선정→문헌조사→방법론→집필→교정 에이전트 팀 하네스.

## Specialist Agents

- `literature-analyst`: 문헌 분석가. 선행연구를 체계적으로 조사하고, 비판적으로 검토하며, 연구의 이론적 틀을 구축한다.
- `methodology-expert`: 연구 방법론 전문가. 연구질문에 적합한 연구설계, 데이터 수집 방법, 분석 기법을 설계하고, 방법론적 엄밀성을 확보한다.
- `proofreader`: 논문 교정자. 문법·맞춤법 교정, 학술 형식 검증, 일관성 검토, 표절 위험 점검을 수행한다.
- `topic-explorer`: 논문 주제 탐색자. 연구 분야의 동향을 파악하고, 연구 갭을 발견하며, 구체적인 연구질문과 가설을 수립한다.
- `writing-coach`: 논문 집필 코치. 논문의 전체 구조를 설계하고, 각 장의 초고를 작성하며, 논증을 강화한다.

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

- `.agents/skills/academic-writing-style/SKILL.md`
- `.agents/skills/research-methodology/SKILL.md`
