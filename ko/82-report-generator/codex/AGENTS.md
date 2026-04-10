# Report Generator Harness Codex 지침

## 목적

- 이 디렉토리는 `Report Generator Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/report-generator/SKILL.md`
- 전문 agent: `.codex/agents/analyst.toml`, `.codex/agents/data-collector.toml`, `.codex/agents/executive-summarizer.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/visualizer.toml`
- 확장 스킬: `.agents/skills/data-visualization-guide/SKILL.md`, `.agents/skills/kpi-dashboard-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `report-generator` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 업무 보고서의 데이터수집→분석→시각화→집필→요약을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_data_collection.md` — 수집된 데이터 정리
- `02_analysis_report.md` — 분석 결과
- `03_visualization_spec.md` — 시각화 명세
- `04_full_report.md` — 최종 보고서
- `05_executive_summary.md` — 경영진 요약 및 검증 보고
