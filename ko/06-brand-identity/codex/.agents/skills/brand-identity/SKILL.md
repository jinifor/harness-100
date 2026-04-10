---
name: brand-identity
description: >-
  Trigger when: 사용자가 `brand-identity` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Brand Identity Harness

브랜드 아이덴티티의 네이밍→슬로건→톤앤매너→가이드라인을 에이전트 팀이 협업하여 설계하는 하네스.

## Specialist Agents

- `brand-strategist`: 브랜드 전략가. 시장 분석, 경쟁 포지셔닝, 타깃 페르소나, 브랜드 아키타입, 차별화 전략을 수립한다.
- `copywriter`: 브랜드 카피라이터. 슬로건, 태그라인, 브랜드 스토리, 톤앤매너 가이드를 작성한다.
- `identity-reviewer`: 브랜드 아이덴티티 검증자(QA). 전략-네이밍-버벌-비주얼 간의 일관성을 교차 검증하고, 브랜드 정합성 문제를 발견한다.
- `naming-specialist`: 브랜드 네이밍 전문가. 브랜드 전략에 기반한 네이밍 후보를 개발하고, 도메인 가용성, 상표 충돌, 발음 용이성을 검토한다.
- `visual-director`: 비주얼 디렉터. 브랜드 컬러 시스템, 타이포그래피, 로고 컨셉, 비주얼 가이드라인을 설계한다.

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
- `01_brand_strategy.md` — 브랜드 전략 보고서
- `02_naming_candidates.md` — 네이밍 후보
- `03_verbal_identity.md` — 버벌 아이덴티티 (슬로건, 톤앤매너)
- `04_visual_identity.md` — 비주얼 아이덴티티 (컬러, 타이포, 로고)
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/brand-archetype/SKILL.md`
- `.agents/skills/color-psychology/SKILL.md`
- `.agents/skills/naming-methodology/SKILL.md`
