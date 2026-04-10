---
name: api-client-generator
description: >-
  Trigger when: 사용자가 `api-client-generator` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# API Client Generator Harness

API 클라이언트 SDK 생성: 스펙파싱→타입생성→클라이언트코드→테스트→사용문서를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `doc-writer`: SDK 문서 작성 전문가. README, 빠른 시작 가이드, API 레퍼런스, 사용 예제, 변경 로그, 마이그레이션 가이드를 작성한다.
- `sdk-developer`: SDK 클라이언트 개발자. HTTP 클라이언트 래퍼, 인증 핸들러, 페이지네이션 헬퍼, 재시도/서킷브레이커 로직, 에러 핸들링을 포함한 프로덕션급 SDK를 개발한다.
- `spec-parser`: API 스펙 파서. OpenAPI(Swagger), GraphQL SDL, gRPC Proto 등 API 명세를 파싱하여 엔드포인트, 모델, 인증 방식, 에러 코드를 체계적으로 추출한다.
- `test-engineer`: SDK 테스트 엔지니어. 단위 테스트, 통합 테스트, 목(mock) 서버 설정, 스냅샷 테스트, 에지 케이스 검증을 수행한다.
- `type-generator`: 타입 생성 전문가. API 스키마를 타깃 언어의 타입 시스템으로 변환한다. 요청/응답 모델, Enum, 유니온 타입, 제네릭, 유틸리티 타입을 생성한다.

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

- `00_input.md` — 사용자 입력 및 API 스펙 정보
- `01_spec_analysis.md` — API 스펙 분석 결과
- `02_types/` — 생성된 타입 정의 파일
- `03_client/` — SDK 클라이언트 코드
- `04_tests/` — 테스트 코드
- `05_docs/` — 사용 문서

## 확장 스킬

- `.agents/skills/openapi-spec-patterns/SKILL.md`
- `.agents/skills/sdk-design-patterns/SKILL.md`
