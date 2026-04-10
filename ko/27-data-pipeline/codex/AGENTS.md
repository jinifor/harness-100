# Data Pipeline Harness Codex 지침

## 목적

- 이 디렉토리는 `Data Pipeline Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/data-pipeline/SKILL.md`
- 전문 agent: `.codex/agents/data-quality-manager.toml`, `.codex/agents/etl-architect.toml`, `.codex/agents/monitoring-specialist.toml`, `.codex/agents/pipeline-reviewer.toml`, `.codex/agents/scheduler-engineer.toml`
- 확장 스킬: `.agents/skills/dag-orchestration-patterns/SKILL.md`, `.agents/skills/data-quality-framework/SKILL.md`

## 실행 원칙

- 전체 작업은 `data-pipeline` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 데이터 파이프라인의 수집→변환→적재→품질검증→모니터링을 에이전트 팀이 협업하여 설계·구현하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_etl_architecture.md` — ETL 아키텍처 설계서
- `02_data_quality_plan.md` — 데이터 품질 관리 계획
- `03_scheduler_config.md` — 스케줄링 설정 및 DAG 정의
- `04_monitoring_setup.md` — 모니터링 대시보드 및 알림 설정
- `05_review_report.md` — 리뷰 보고서
- `pipeline_code/` — 파이프라인 구현 코드
