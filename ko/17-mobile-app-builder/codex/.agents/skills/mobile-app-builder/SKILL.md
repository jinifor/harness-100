---
name: mobile-app-builder
description: >-
  Trigger when: 사용자가 `mobile-app-builder` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Mobile App Builder Harness

모바일 앱의 UI/UX 설계→네이티브 코드 생성→API 연동→스토어 배포 준비를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `api-integrator`: API 연동 전문가. REST/GraphQL API 클라이언트를 구현하고, 인증(OAuth, JWT), 캐싱, 오프라인 지원, 에러 핸들링을 설계한다. 서버와 앱 사이의 데이터 흐름을 최적화한다.
- `app-developer`: 모바일 앱 개발자. Swift/SwiftUI, Kotlin/Jetpack Compose, Flutter, React Native 등 네이티브/크로스플랫폼 코드를 생성한다. 아키텍처 패턴(MVVM, Clean Architecture)을 적용하고 테스트 가능한 구조로 구현한다.
- `qa-engineer`: 모바일 QA 엔지니어. UI 테스트, 성능 테스트, 접근성 검증, 보안 점검, 플랫폼 호환성 테스트를 수행한다. 모든 산출물 간 정합성을 교차 검증한다.
- `store-manager`: 앱 스토어 배포 매니저. App Store Connect와 Google Play Console에 필요한 메타데이터, 스크린샷 가이드, 개인정보처리방침, 심사 대응 전략을 준비한다.
- `ux-designer`: 모바일 UX/UI 설계자. 와이어프레임, 디자인 시스템, 네비게이션 구조, 인터랙션 패턴을 설계한다. iOS HIG와 Material Design 가이드라인을 준수하며, 접근성(A11y)을 고려한 설계를 수행한다.

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
- `01_ux_design.md` — UX/UI 설계 문서
- `02_app_code/` — 앱 소스 코드
- `02_app_architecture.md` — 앱 아키텍처 문서
- `03_api_integration.md` — API 연동 명세
- `04_store_listing.md` — 스토어 배포 메타데이터
- `05_qa_report.md` — QA 검증 보고서

## 확장 스킬

- `.agents/skills/app-store-optimization/SKILL.md`
- `.agents/skills/mobile-ux-patterns/SKILL.md`
