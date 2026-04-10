---
name: report-generator
description: >-
  Trigger when: 사용자가 `report-generator` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Report Generator Harness

업무 보고서의 데이터수집→분석→시각화→집필→요약을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `analyst`: 업무 보고서 분석가. 수집된 데이터에서 통계적 분석, 트렌드 파악, 비교 분석, 인사이트 도출을 수행하여 보고서의 핵심 논거를 구성한다.
- `data-collector`: 업무 보고서 데이터 수집가. 보고서에 필요한 정량·정성 데이터를 웹 검색, 파일 분석, 사용자 제공 자료에서 체계적으로 수집하고 정제한다.
- `executive-summarizer`: 업무 보고서 요약 및 교차 검증 전문가(QA). 경영진용 1페이지 요약을 작성하고, 데이터-분석-시각화-본문 간 정합성을 교차 검증한다.
- `report-writer`: 업무 보고서 작성자. 분석 결과와 시각화를 통합하여 논리적이고 설득력 있는 보고서를 집필한다. 보고 대상(경영진/실무자/외부)에 맞는 톤과 구조를 적용한다.
- `visualizer`: 업무 보고서 시각화 전문가. 분석 결과를 차트, 테이블, 다이어그램으로 변환하는 명세를 작성하고, Mermaid/ASCII 차트로 시각화를 구현한다.

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
- `01_data_collection.md` — 수집된 데이터 정리
- `02_analysis_report.md` — 분석 결과
- `03_visualization_spec.md` — 시각화 명세
- `04_full_report.md` — 최종 보고서
- `05_executive_summary.md` — 경영진 요약 및 검증 보고

## 확장 스킬

- `.agents/skills/data-visualization-guide/SKILL.md`
- `.agents/skills/kpi-dashboard-patterns/SKILL.md`
