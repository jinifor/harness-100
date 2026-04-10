---
name: competency-modeler
description: >-
  Trigger when: 사용자가 `competency-modeler` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Competency Modeler Harness

역량 모델링의 직무분석→역량사전작성→평가루브릭설계→개발계획수립→역량매트릭스를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `competency-architect`: 역량사전 작성자. 직무 분석 결과를 바탕으로 역량을 정의하고, 행동지표를 작성하며, 수준 체계를 설계한다.
- `development-planner`: 역량 개발 계획 수립자. 역량 갭 분석을 기반으로 개인/조직 차원의 역량 개발 계획을 수립하고, 역량 매트릭스를 작성한다.
- `job-analyst`: 직무 분석가. 직무기술서 작성, 핵심 과업 분석, 필요 지식·기술·태도(KSA) 도출을 수행한다.
- `rubric-designer`: 평가 루브릭 설계자. 역량별 평가 기준, 채점표, 평가 도구를 설계한다.

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
- `01_job_analysis.md` — 직무 분석서
- `02_competency_dictionary.md` — 역량 사전
- `03_assessment_rubric.md` — 평가 루브릭
- `04_development_plan.md` — 역량 개발 계획서
- `05_competency_matrix.md` — 역량 매트릭스

## 확장 스킬

- `.agents/skills/bars-assessment/SKILL.md`
- `.agents/skills/ksa-taxonomy/SKILL.md`
