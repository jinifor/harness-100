---
name: code-reviewer
description: >-
  Trigger when: 사용자가 `code-reviewer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Code Reviewer Harness

코드 리뷰 자동화의 스타일→보안→성능→아키텍처 리뷰를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `architecture-reviewer`: 아키텍처 리뷰어. 설계 패턴, SOLID 원칙, 의존성 방향, 결합도/응집도, 모듈 구조, 테스트 가능성, 확장성을 분석한다.
- `performance-analyst`: 코드 성능 분석가. 시간/공간 복잡도, 메모리 릭, 동시성 문제, DB 쿼리 최적화, 불필요한 연산, 캐싱 기회를 분석한다.
- `review-synthesizer`: 코드 리뷰 종합자(QA). 스타일·보안·성능·아키텍처 리뷰 결과를 종합하고, 우선순위를 판정하며, 영역 간 정합성을 확인한다.
- `security-analyst`: 코드 보안 분석가. OWASP Top 10, 인젝션 취약점, 인증/인가 결함, 민감 데이터 노출, 안전하지 않은 직렬화, 의존성 취약점을 분석한다.
- `style-inspector`: 코드 스타일 검사관. 코딩 컨벤션, 포맷팅, 네이밍 규칙, 주석 품질, 가독성, 일관성을 검사한다. 언어별 스타일 가이드(PEP 8, Airbnb JS, Google Java 등)에 정통하다.

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
- `01_style_review.md` — 코드 스타일 리뷰
- `02_security_review.md` — 보안 리뷰
- `03_performance_review.md` — 성능 리뷰
- `04_architecture_review.md` — 아키텍처 리뷰
- `05_review_summary.md` — 종합 리뷰 보고서

## 확장 스킬

- `.agents/skills/refactoring-catalog/SKILL.md`
- `.agents/skills/vulnerability-patterns/SKILL.md`
