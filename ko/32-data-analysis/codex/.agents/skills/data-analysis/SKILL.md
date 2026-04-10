---
name: data-analysis
description: >-
  Trigger when: 사용자가 `data-analysis` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Data Analysis Harness

데이터 분석 프로젝트의 탐색→정제→분석→시각화→보고서를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `analyst`: 통계 분석 전문가. 가설검정, 상관분석, 회귀분석, 클러스터링, 시계열 분석 등 목적에 맞는 통계 기법을 적용하고 결과를 해석한다.
- `cleaner`: 데이터 정제 전문가. 결측치 처리, 이상치 처리, 타입 변환, 중복 제거, 정규화/표준화를 수행하고, 모든 변환을 재현 가능한 코드로 기록한다.
- `explorer`: 탐색적 데이터 분석(EDA) 전문가. 데이터 프로파일링, 분포 분석, 이상치 탐지, 변수 간 관계 파악, 데이터 품질 진단을 수행한다.
- `reporter`: 분석 보고서 작성 전문가. EDA, 정제, 분석, 시각화 결과를 종합하여 경영진/이해관계자를 위한 최종 보고서를 작성한다. 인사이트와 권고안을 비전문가도 이해할 수 있게 전달한다.
- `visualizer`: 데이터 시각화 전문가. 분석 결과를 효과적으로 전달하는 차트를 설계하고, matplotlib/seaborn/plotly 코드를 생성한다.

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

- `00_input.md` — 사용자 입력 및 데이터 소스 정리
- `01_exploration_report.md` — 탐색적 데이터 분석(EDA) 결과
- `02_cleaning_log.md` — 정제 작업 로그 및 변환 코드
- `03_analysis_results.md` — 통계 분석 결과
- `04_visualizations.md` — 시각화 컨셉 및 코드
- `05_final_report.md` — 최종 분석 보고서
- `scripts/` — 재현 가능한 분석 스크립트

## 확장 스킬

- `.agents/skills/statistical-tests-selector/SKILL.md`
- `.agents/skills/visualization-chooser/SKILL.md`
