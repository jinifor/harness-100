---
name: design-system
description: >-
  Trigger when: 사용자가 `design-system` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Design System Harness

UI 디자인 시스템 구축: 디자인토큰→컴포넌트라이브러리→스토리북→접근성검증→문서를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `a11y-auditor`: 접근성(A11y) 검증 전문가. WCAG 2.1 AA/AAA 준수 여부를 검증하고, ARIA 패턴, 키보드 네비게이션, 스크린리더 호환성, 색상 대비를 체계적으로 점검한다.
- `component-developer`: UI 컴포넌트 개발 전문가. React/Vue 기반 재사용 가능한 컴포넌트를 설계하고 구현한다. 변형(variant), 합성(composition), 상태 관리, 제어/비제어 패턴을 포함한다.
- `doc-writer`: 디자인 시스템 문서 작성 전문가. 설계 원칙, 컴포넌트 사용 가이드, 디자인-개발 핸드오프 가이드, 기여 가이드, 버전 관리 정책을 작성한다.
- `storybook-builder`: 스토리북 빌더. 각 컴포넌트의 스토리, 인터랙션 테스트, 문서 페이지를 작성하고, 디자인 토큰 시각화와 테마 전환을 스토리북에 구현한다.
- `token-designer`: 디자인 토큰 설계 전문가. 색상, 타이포그래피, 간격, 그림자, 모션, 반응형 브레이크포인트 등 디자인 시스템의 기반이 되는 토큰을 체계적으로 설계한다.

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

- `00_input.md` — 사용자 입력 및 브랜드 정보
- `01_design_tokens/` — 디자인 토큰 정의 파일
- `02_components/` — 컴포넌트 라이브러리 코드
- `03_storybook/` — 스토리북 스토리 및 설정
- `04_a11y_report.md` — 접근성 검증 보고서
- `05_docs/` — 디자인 시스템 문서

## 확장 스킬

- `.agents/skills/token-generator/SKILL.md`
- `.agents/skills/wcag-checker/SKILL.md`
