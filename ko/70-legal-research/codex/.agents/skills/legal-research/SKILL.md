---
name: legal-research
description: >-
  Trigger when: 사용자가 `legal-research` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Legal Research Harness

법률 리서치 — 판례검색→법리분석→의견서→전략수립을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `case-searcher`: 판례 검색자. 법률 이슈와 관련된 판례를 체계적으로 검색하고, 요지를 정리하며, 판례 동향을 분석한다.
- `legal-analyst`: 법리 분석가. 판례에서 도출된 법리를 분석하고, 쟁점별 법적 논리를 구축하며, 학설과 판례의 관계를 정리한다.
- `opinion-writer`: 의견서 작성자. 법리 분석 결과를 기반으로 논리적이고 설득력 있는 법률 의견서를 작성한다.
- `strategy-advisor`: 법률 전략 수립자. 법리 분석과 의견서를 기반으로 소송/분쟁 대응 전략, 리스크 평가, 대안적 분쟁 해결 방안을 수립한다.

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

- `00_input.md` — 사용자 입력 정리 (법률 이슈)
- `01_case_search.md` — 판례 검색 보고서
- `02_legal_analysis.md` — 법리 분석 보고서
- `03_legal_opinion.md` — 법률 의견서
- `04_legal_strategy.md` — 전략 수립 보고서

## 확장 스킬

- `.agents/skills/case-analysis-framework/SKILL.md`
- `.agents/skills/legal-writing-methodology/SKILL.md`
