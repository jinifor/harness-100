---
name: data-pipeline
description: >-
  Trigger when: 사용자가 `data-pipeline` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Data Pipeline Harness

데이터 파이프라인의 수집→변환→적재→품질검증→모니터링을 에이전트 팀이 협업하여 설계·구현하는 하네스.

## Specialist Agents

- `data-quality-manager`: 데이터 품질 관리자. 데이터 프로파일링, 검증 규칙 설계, 이상 탐지 로직, 데이터 계보 추적을 수행하여 파이프라인 전 구간의 데이터 신뢰성을 보장한다.
- `etl-architect`: ETL 아키텍처 설계자. 데이터 소스 분석, 스키마 설계, 수집·변환·적재 파이프라인 구조를 설계하고, 기술 스택을 선정하며, 구현 코드를 생성한다.
- `monitoring-specialist`: 모니터링 전문가. 파이프라인 실행 메트릭, 데이터 품질 대시보드, 알림 체계, SLA 추적, 장애 대응 런북을 설계하여 파이프라인의 관측 가능성을 확보한다.
- `pipeline-reviewer`: 파이프라인 리뷰어(QA). ETL설계-품질계획-스케줄링-모니터링 간의 정합성을 교차 검증하고, 운영 준비도를 평가하며, 누락·모순·위험 요소를 발견하여 피드백을 제공한다.
- `scheduler-engineer`: 스케줄링 엔지니어. DAG 설계, 작업 의존관계 관리, 재시도 전략, 리소스 할당, 백필 전략을 수립하여 파이프라인의 안정적 자동 실행을 보장한다.

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
- `01_etl_architecture.md` — ETL 아키텍처 설계서
- `02_data_quality_plan.md` — 데이터 품질 관리 계획
- `03_scheduler_config.md` — 스케줄링 설정 및 DAG 정의
- `04_monitoring_setup.md` — 모니터링 대시보드 및 알림 설정
- `05_review_report.md` — 리뷰 보고서
- `pipeline_code/` — 파이프라인 구현 코드

## 확장 스킬

- `.agents/skills/dag-orchestration-patterns/SKILL.md`
- `.agents/skills/data-quality-framework/SKILL.md`
