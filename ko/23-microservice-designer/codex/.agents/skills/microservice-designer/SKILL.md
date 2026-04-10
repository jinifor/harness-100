---
name: microservice-designer
description: >-
  Trigger when: 사용자가 `microservice-designer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Microservice Designer Harness

마이크로서비스 아키텍처를 설계·분해·통신·모니터링하는 에이전트 팀 하네스. 도메인 분석부터 관측성 설계까지 풀 파이프라인을 자동화한다.

## Specialist Agents

- `architecture-reviewer`: 마이크로서비스 아키텍처 리뷰어(QA). 도메인-서비스-통신-관측성 간의 정합성을 교차 검증하고, 분산 시스템의 잠재 위험을 식별한다.
- `communication-designer`: 서비스 간 통신 설계 전문가. 동기/비동기 통신 패턴을 선정하고, 이벤트 버스를 설계하며, API 게이트웨이와 서비스 메시를 구성한다.
- `domain-analyst`: 도메인 분석 전문가. 비즈니스 도메인을 DDD 관점에서 분석하고, 바운디드 컨텍스트를 식별하며, 이벤트 스토밍으로 도메인 이벤트와 애그리거트를 도출한다.
- `observability-engineer`: 관측성 설계 전문가. 분산 시스템의 메트릭, 로깅, 트레이싱 전략을 수립하고, 알림 규칙과 대시보드를 설계한다.
- `service-architect`: 마이크로서비스 설계 전문가. 바운디드 컨텍스트를 서비스로 매핑하고, API 계약을 정의하며, 데이터 소유권과 배포 단위를 설계한다.

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
- `01_domain_analysis.md` — 도메인 분석 보고서
- `02_service_design.md` — 서비스 설계서
- `03_communication_design.md` — 통신 설계서
- `04_observability_design.md` — 관측성 설계서
- `05_review_report.md` — 최종 리뷰 보고서

## 확장 스킬

- `.agents/skills/ddd-context-mapping/SKILL.md`
- `.agents/skills/distributed-patterns/SKILL.md`
