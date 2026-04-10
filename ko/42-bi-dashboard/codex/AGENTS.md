# BI Dashboard Harness Codex 지침

## 목적

- 이 디렉토리는 `BI Dashboard Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/bi-dashboard/SKILL.md`
- 전문 agent: `.codex/agents/bi-reviewer.toml`, `.codex/agents/dashboard-builder.toml`, `.codex/agents/data-engineer.toml`, `.codex/agents/kpi-designer.toml`, `.codex/agents/report-automator.toml`
- 확장 스킬: `.agents/skills/chart-selector/SKILL.md`, `.agents/skills/kpi-tree-builder/SKILL.md`

## 실행 원칙

- 전체 작업은 `bi-dashboard` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- BI 대시보드 구축의 데이터웨어하우스 설계→KPI 정의→시각화→자동 보고를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_data_warehouse_design.md` — 데이터 웨어하우스 설계서
- `02_kpi_definition.md` — KPI 정의서
- `03_dashboard_spec.md` — 대시보드 시각화 명세
- `04_report_automation.md` — 자동 보고 설정서
- `05_review_report.md` — 검증 보고서
