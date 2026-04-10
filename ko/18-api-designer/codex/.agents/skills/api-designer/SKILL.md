---
name: api-designer
description: >-
  Trigger when: 사용자가 `api-designer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# API Designer Harness

REST/GraphQL API의 설계·문서화·목업·테스트를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `api-architect`: API 아키텍트. 리소스 모델링, 엔드포인트 설계, URL 네이밍, HTTP 메서드 매핑, 버전 관리 전략, 페이지네이션, 필터링을 설계한다. REST와 GraphQL 양쪽 패러다임에 정통하다.
- `doc-writer`: API 문서 작성자. 개발자 친화적인 API 문서를 작성한다. 빠른 시작 가이드, 인증 설명, 엔드포인트별 요청/응답 예시, 에러 코드 레퍼런스, SDK 사용법을 포함한다.
- `mock-tester`: API 목업 및 테스트 전문가. Mock 서버 설정, 통합 테스트 시나리오, 부하 테스트 설계, 계약 테스트(Contract Testing)를 수행한다.
- `review-auditor`: API 리뷰 감사자(QA). 보안, 일관성, 성능, RESTful 베스트 프랙티스 준수를 교차 검증한다. 설계-스키마-문서-테스트 간 정합성을 확인한다.
- `schema-validator`: API 스키마 검증자. OpenAPI 3.1/GraphQL SDL 스키마를 생성하고, 타입 안전성, 필수/선택 필드, 데이터 형식(날짜, 이메일 등), 열거형, 참조 관계를 검증한다.

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
- `01_api_design.md` — API 설계 문서
- `02_schema.yaml` — OpenAPI/GraphQL 스키마 파일
- `03_api_docs.md` — API 개발자 문서
- `04_mock_tests.md` — 목업 서버 설정 및 테스트 결과
- `05_review_report.md` — API 리뷰 보고서

## 확장 스킬

- `.agents/skills/api-error-design/SKILL.md`
- `.agents/skills/rest-api-conventions/SKILL.md`
