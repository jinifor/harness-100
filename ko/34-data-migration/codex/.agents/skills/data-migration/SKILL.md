---
name: data-migration
description: >-
  Trigger when: 사용자가 `data-migration` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Data Migration Harness

데이터 마이그레이션: 소스분석→스키마매핑→변환스크립트생성→검증쿼리→롤백계획을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `rollback-planner`: 롤백 및 비상 대응 전문가. 백업 전략, 롤백 스크립트, 비상 절차, 의사결정 트리, 커뮤니케이션 계획을 수립한다.
- `schema-mapper`: 스키마 매핑 전문가. 소스와 타깃 간 필드 매핑, 타입 변환 규칙, 비즈니스 변환 로직, 기본값 정의를 체계적으로 설계한다.
- `script-developer`: 마이그레이션 스크립트 개발자. ETL 변환 코드, 증분 마이그레이션 로직, 배치 처리, 성능 최적화를 포함한 실행 가능한 스크립트를 생성한다.
- `source-analyst`: 소스 시스템 분석 전문가. 소스 데이터베이스의 스키마 역공학, 데이터 프로파일링, 테이블 간 의존성 매핑, 데이터 품질 진단을 수행한다.
- `validation-engineer`: 마이그레이션 검증 엔지니어. 데이터 정합성 검증 쿼리, 행 수 일치 검증, 비즈니스 규칙 검증, 회귀 테스트 스위트를 설계하고 실행한다.

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

- `00_input.md` — 사용자 입력 및 마이그레이션 요구사항
- `01_source_analysis.md` — 소스 시스템 분석 보고서
- `02_schema_mapping.md` — 스키마 매핑 명세서
- `03_migration_scripts/` — 변환 스크립트 디렉토리
- `04_validation_suite.md` — 검증 쿼리 및 테스트 스위트
- `05_rollback_plan.md` — 롤백 및 비상 대응 계획

## 확장 스킬

- `.agents/skills/data-validation-patterns/SKILL.md`
- `.agents/skills/type-mapping-encyclopedia/SKILL.md`
