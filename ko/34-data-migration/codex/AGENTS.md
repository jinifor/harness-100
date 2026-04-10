# Data Migration Harness Codex 지침

## 목적

- 이 디렉토리는 `Data Migration Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/data-migration/SKILL.md`
- 전문 agent: `.codex/agents/rollback-planner.toml`, `.codex/agents/schema-mapper.toml`, `.codex/agents/script-developer.toml`, `.codex/agents/source-analyst.toml`, `.codex/agents/validation-engineer.toml`
- 확장 스킬: `.agents/skills/data-validation-patterns/SKILL.md`, `.agents/skills/type-mapping-encyclopedia/SKILL.md`

## 실행 원칙

- 전체 작업은 `data-migration` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 데이터 마이그레이션: 소스분석→스키마매핑→변환스크립트생성→검증쿼리→롤백계획을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 및 마이그레이션 요구사항
- `01_source_analysis.md` — 소스 시스템 분석 보고서
- `02_schema_mapping.md` — 스키마 매핑 명세서
- `03_migration_scripts/` — 변환 스크립트 디렉토리
- `04_validation_suite.md` — 검증 쿼리 및 테스트 스위트
- `05_rollback_plan.md` — 롤백 및 비상 대응 계획
