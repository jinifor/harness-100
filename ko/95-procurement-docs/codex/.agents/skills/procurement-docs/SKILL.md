---
name: procurement-docs
description: >-
  Trigger when: 사용자가 `procurement-docs` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Procurement Docs Harness

구매 문서세트 생성 하네스. 요구사항 정의부터 벤더 비교표, 평가 기준표, 계약 조건 검토, 검수 기준서까지 에이전트 팀이 협업하여 생성한다.

## Specialist Agents

- `acceptance-builder`: 검수 기준서 작성 전문가. 납품물의 검수 항목, 테스트 절차, 합격/불합격 판정 기준을 설계하여 객관적인 검수가 가능하도록 한다.
- `contract-reviewer`: 계약 조건 검토 전문가. 구매 계약의 약관, 리스크 조항, SLA, 지적재산권, 해지 조건 등을 분석하고 협상 포인트를 도출한다.
- `evaluation-designer`: 평가 기준표 설계 전문가. 벤더/제품 선정을 위한 평가 기준, 배점, 가중치를 설계하고, 정성·정량 평가 방법론과 합의 의사결정 프로세스를 구축한다.
- `requirements-definer`: 구매 요구사항 정의 전문가. 구매 대상의 기술 사양, 수량, 납기, 예산, 필수/선택 요건을 체계적으로 정의하여 벤더 선정의 기초 문서를 작성한다.
- `vendor-comparator`: 벤더 비교 분석 전문가. 구매 요구사항에 부합하는 벤더/제품 후보를 조사하고, 기능·가격·실적·지원 등 다각도 비교표를 작성한다.

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

- `00_input.md` — 구매 요청 및 배경 정리
- `01_requirements_spec.md` — 구매 요구사항 정의서
- `02_vendor_comparison.md` — 벤더 비교 분석표
- `03_evaluation_criteria.md` — 평가 기준표
- `04_contract_review.md` — 계약 조건 검토서
- `05_acceptance_criteria.md` — 검수 기준서
- `06_procurement_summary.md` — 구매 종합 보고서

## 확장 스킬

- `.agents/skills/contract-checklist/SKILL.md`
- `.agents/skills/vendor-scoring/SKILL.md`
