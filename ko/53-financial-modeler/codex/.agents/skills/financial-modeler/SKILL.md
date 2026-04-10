---
name: financial-modeler
description: >-
  Trigger when: 사용자가 `financial-modeler` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Financial Modeler Harness

수익 모델, 비용 구조, 시나리오 분석, 밸류에이션까지 재무 모델링 전 과정을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `cost-analyst`: 비용 구조 분석 전문가. 고정비·변동비를 구분하고, 원가 구조를 설계하여 손익분기점을 산출하고 비용 최적화 방안을 도출한다.
- `model-reviewer`: 재무 모델 리뷰어(QA). 수익 모델-비용 구조-시나리오-밸류에이션 간의 수식 정합성, 가정 일관성, 논리적 타당성을 교차 검증한다.
- `revenue-modeler`: 수익 모델 설계 전문가. 사업의 수익원을 정의하고, 가격 전략, 판매량 추정, 성장률 시나리오를 수립하여 매출 예측 모델을 구축한다.
- `scenario-planner`: 재무 시나리오 분석 전문가. Base/Bull/Bear 시나리오를 구성하고, 핵심 변수의 민감도 분석을 수행하여 재무 성과의 변동 범위를 산출한다.
- `valuation-expert`: 밸류에이션 전문가. DCF, 멀티플, 비교 기업 분석 등 다양한 밸류에이션 방법론을 적용하여 기업 가치를 산출하고, 투자 판단의 기초를 제공한다.

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

- `.agents/skills/dcf-valuation/SKILL.md`
- `.agents/skills/sensitivity-analysis/SKILL.md`
- `.agents/skills/unit-economics/SKILL.md`
