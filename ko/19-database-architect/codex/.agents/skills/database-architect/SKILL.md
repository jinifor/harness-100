---
name: database-architect
description: >-
  Trigger when: 사용자가 `database-architect` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Database Architect Harness

DB 설계의 모델링→마이그레이션→인덱싱→쿼리 최적화를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `data-modeler`: 데이터 모델러. ERD 설계, 정규화/비정규화 전략, 테이블 관계(1:1, 1:N, N:M) 설계, 데이터 타입 선정, 제약조건 정의를 수행한다. RDBMS(PostgreSQL, MySQL)와 NoSQL(MongoDB, DynamoDB) 양쪽에 정통하다.
- `integration-reviewer`: 통합 리뷰어(QA). 데이터 모델-마이그레이션-성능-보안 간의 정합성을 교차 검증하고, 운영 준비성을 평가한다.
- `migration-manager`: 마이그레이션 관리자. DDL 스크립트 생성, 마이그레이션 버전 관리, 롤백 전략, 시드 데이터 생성, 무중단 마이그레이션(zero-downtime migration) 절차를 설계한다.
- `performance-analyst`: DB 성능 분석가. 인덱스 전략, 쿼리 최적화, 실행 계획(EXPLAIN) 분석, 파티셔닝, 커넥션 풀링, 캐싱 전략을 설계한다.
- `security-auditor`: DB 보안 감사자. 접근 제어(RBAC), 데이터 암호화(TDE, 컬럼 암호화), SQL 인젝션 방어, 감사 로깅, 백업/복구 전략을 검증하고 설계한다.

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
- `01_data_model.md` — 데이터 모델 설계 문서
- `02_migration.sql` — 마이그레이션 SQL 스크립트
- `02_migration_plan.md` — 마이그레이션 계획서
- `03_performance.md` — 성능 최적화 보고서
- `04_security.md` — 보안 검증 보고서
- `05_review_report.md` — 통합 리뷰 보고서

## 확장 스킬

- `.agents/skills/normalization-patterns/SKILL.md`
- `.agents/skills/query-optimization-catalog/SKILL.md`
