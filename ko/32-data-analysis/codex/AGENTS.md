# Data Analysis Harness Codex 지침

## 목적

- 이 디렉토리는 `Data Analysis Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/data-analysis/SKILL.md`
- 전문 agent: `.codex/agents/analyst.toml`, `.codex/agents/cleaner.toml`, `.codex/agents/explorer.toml`, `.codex/agents/reporter.toml`, `.codex/agents/visualizer.toml`
- 확장 스킬: `.agents/skills/statistical-tests-selector/SKILL.md`, `.agents/skills/visualization-chooser/SKILL.md`

## 실행 원칙

- 전체 작업은 `data-analysis` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 데이터 분석 프로젝트의 탐색→정제→분석→시각화→보고서를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 및 데이터 소스 정리
- `01_exploration_report.md` — 탐색적 데이터 분석(EDA) 결과
- `02_cleaning_log.md` — 정제 작업 로그 및 변환 코드
- `03_analysis_results.md` — 통계 분석 결과
- `04_visualizations.md` — 시각화 컨셉 및 코드
- `05_final_report.md` — 최종 분석 보고서
- `scripts/` — 재현 가능한 분석 스크립트
