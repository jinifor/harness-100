---
name: contract-analyzer
description: >-
  Trigger when: 사용자가 `contract-analyzer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Contract Analyzer Harness

계약서 분석·작성·검토·위험 평가를 에이전트 팀이 협업하여 수행하는 하네스. 조항 분석부터 리스크 평가, 비교 검토, 수정 제안까지 계약 관리 전 과정을 체계적으로 처리한다.

## Specialist Agents

- `clause-analyst`: 조항 분석가. 계약서의 구조를 파악하고, 각 조항의 법적 의미·효력·적용 범위를 분석하며, 누락된 필수 조항을 식별한다.
- `clause-drafter`: 조항 작성·수정 전문가. 표준 계약 조항을 작성하고, 기존 조항의 개선안을 제시하며, 당사자의 이익을 보호하는 조항을 설계한다.
- `comparison-reviewer`: 비교 검토자. 계약서를 업계 표준, 이전 버전, 또는 상대방 초안과 비교하여 차이점을 분석하고 협상 포인트를 도출한다.
- `contract-coordinator`: 계약 조율자(QA). 조항 분석·수정안·리스크 평가·비교 검토를 종합하여 최종 법률 의견서를 작성하고, 산출물 간 정합성을 검증한다.
- `risk-assessor`: 리스크 평가자. 계약서의 법적·사업적 위험을 식별하고, 불리한 조항을 발견하며, 리스크 완화 전략을 제시한다.

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

- `00_input.md` — 사용자 입력 정리 (계약 유형, 당사자, 요구사항)
- `01_clause_analysis.md` — 조항 분석서
- `02_draft_clauses.md` — 조항 작성/수정안
- `03_risk_assessment.md` — 리스크 평가 보고서
- `04_comparison_report.md` — 비교 검토 보고서
- `05_final_opinion.md` — 종합 법률 의견서

## 확장 스킬

- `.agents/skills/clause-risk-database/SKILL.md`
- `.agents/skills/negotiation-playbook/SKILL.md`
