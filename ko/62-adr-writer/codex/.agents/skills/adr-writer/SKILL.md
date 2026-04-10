---
name: adr-writer
description: >-
  Trigger when: 사용자가 `adr-writer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# ADR Writer Harness

아키텍처 결정 기록(ADR) 작성 에이전트 팀 하네스.

## Specialist Agents

- `adr-author`: ADR 문서 작성자. 컨텍스트 분석, 대안 조사, 트레이드오프 평가 결과를 종합하여 표준 ADR 포맷의 공식 아키텍처 결정 기록을 작성한다.
- `alternative-researcher`: 대안 조사원. 아키텍처 결정에 대한 기술 옵션을 탐색하고, 각 대안의 특성·성숙도·커뮤니티·사례를 조사하여 비교 가능한 형태로 정리한다.
- `context-analyst`: 기술 컨텍스트 분석가. 현재 시스템 아키텍처를 파악하고, 결정이 필요한 문제를 정의하며, 기술적·조직적·비즈니스 제약 조건을 식별한다.
- `impact-tracker`: 영향 추적자. 아키텍처 결정이 시스템·팀·프로세스에 미치는 영향을 분석하고, 실행 계획·마이그레이션 로드맵·모니터링 기준을 수립한다.
- `tradeoff-evaluator`: 트레이드오프 평가자. 대안들 간의 정량적·정성적 비교 분석을 수행하고, 품질 속성별 가중 평가 매트릭스를 생성하여 최적 대안을 권고한다.

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

- `.agents/skills/madr-template-engine/SKILL.md`
- `.agents/skills/quality-attribute-analyzer/SKILL.md`
