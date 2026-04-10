---
name: bi-dashboard
description: >-
  Trigger when: 사용자가 `bi-dashboard` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# BI Dashboard Harness

BI 대시보드 구축의 데이터웨어하우스 설계→KPI 정의→시각화→자동 보고를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `bi-reviewer`: BI 검증자(QA). 데이터 모델-KPI 계산-시각화-보고서 간의 정합성을 교차 검증하고, 데이터 오류·지표 모순·UX 문제를 발견하여 피드백을 제공한다.
- `dashboard-builder`: 대시보드 빌더. KPI를 효과적으로 시각화하는 대시보드 레이아웃, 차트 유형, 인터랙션, 색상 체계를 설계한다.
- `data-engineer`: BI 데이터 엔지니어. 원천 데이터 분석, 데이터 웨어하우스 스키마 설계, ETL 파이프라인 정의, 데이터 품질 규칙 수립을 수행한다.
- `kpi-designer`: KPI 설계자. 비즈니스 목표에서 핵심 성과 지표를 도출하고, 계산 로직·목표치·벤치마크·드릴다운 경로를 정의한다.
- `report-automator`: 보고서 자동화 전문가. 정기 보고서 생성, 알림 규칙 설정, 배포 채널 관리, 데이터 스토리텔링 템플릿을 구축한다.

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
- `01_data_warehouse_design.md` — 데이터 웨어하우스 설계서
- `02_kpi_definition.md` — KPI 정의서
- `03_dashboard_spec.md` — 대시보드 시각화 명세
- `04_report_automation.md` — 자동 보고 설정서
- `05_review_report.md` — 검증 보고서

## 확장 스킬

- `.agents/skills/chart-selector/SKILL.md`
- `.agents/skills/kpi-tree-builder/SKILL.md`
