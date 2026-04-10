---
name: startup-launcher
description: >-
  Trigger when: 사용자가 `startup-launcher` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Startup Launcher Harness

스타트업 런칭의 아이디어 검증→비즈니스 모델→MVP→피칭→투자 유치를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `business-modeler`: 비즈니스 모델러. Business Model Canvas 작성, 수익 모델 설계, 유닛 이코노믹스 분석, 재무 예측을 수행한다.
- `launch-reviewer`: 런칭 검증자(QA). 시장분석-비즈니스모델-MVP-피치덱 간의 논리적 일관성, 투자 준비도, 실행 가능성을 교차 검증한다.
- `market-analyst`: 스타트업 시장 분석가. 아이디어 검증, 시장 규모 산정(TAM/SAM/SOM), 경쟁 분석, 고객 페르소나 정의, PMF 가설 수립을 수행한다.
- `mvp-architect`: MVP 설계자. 핵심 기능 우선순위화, 기술 스택 선정, 개발 로드맵 수립, 사용자 플로우 설계를 수행한다.
- `pitch-creator`: 피치덱 작성자. 투자자 대상 프레젠테이션 스토리라인 설계, 슬라이드 구성, 핵심 내러티브 구축을 수행한다.

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
- `01_market_validation.md` — 시장 검증 보고서
- `02_business_model.md` — 비즈니스 모델 설계서
- `03_mvp_blueprint.md` — MVP 설계도
- `04_pitch_deck.md` — 피치덱
- `05_review_report.md` — 런칭 검증 보고서

## 확장 스킬

- `.agents/skills/pitch-deck-framework/SKILL.md`
- `.agents/skills/unit-economics-calculator/SKILL.md`
