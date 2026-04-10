# Database Architect Harness Codex 지침

## 목적

- 이 디렉토리는 `Database Architect Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/database-architect/SKILL.md`
- 전문 agent: `.codex/agents/data-modeler.toml`, `.codex/agents/integration-reviewer.toml`, `.codex/agents/migration-manager.toml`, `.codex/agents/performance-analyst.toml`, `.codex/agents/security-auditor.toml`
- 확장 스킬: `.agents/skills/normalization-patterns/SKILL.md`, `.agents/skills/query-optimization-catalog/SKILL.md`

## 실행 원칙

- 전체 작업은 `database-architect` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- DB 설계의 모델링→마이그레이션→인덱싱→쿼리 최적화를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_data_model.md` — 데이터 모델 설계 문서
- `02_migration.sql` — 마이그레이션 SQL 스크립트
- `02_migration_plan.md` — 마이그레이션 계획서
- `03_performance.md` — 성능 최적화 보고서
- `04_security.md` — 보안 검증 보고서
- `05_review_report.md` — 통합 리뷰 보고서
