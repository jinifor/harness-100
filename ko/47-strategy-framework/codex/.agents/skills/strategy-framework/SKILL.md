---
name: strategy-framework
description: >-
  Trigger when: 사용자가 `strategy-framework` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Strategy Framework Harness

조직의 전략 프레임워크를 OKR설계→BSC매핑→SWOT분석→비전·미션선언문→전략실행로드맵 순으로 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `bsc-analyst`: BSC(Balanced Scorecard) 분석가. OKR 체계를 재무·고객·내부프로세스·학습성장의 4대 관점으로 매핑하고, 관점 간 인과관계와 전략맵을 설계한다.
- `okr-designer`: OKR 설계 전문가. 조직의 전략적 방향을 Objective(목표)와 Key Result(핵심결과)로 구조화하고, 상위-하위 OKR 간 정렬(Alignment)을 설계한다.
- `strategy-reviewer`: 전략 프레임워크 리뷰어(QA). OKR-BSC-SWOT-비전미션-로드맵 간의 논리적 정합성을 교차 검증하고, 전략적 모순·누락·품질 문제를 발견하여 피드백한다.
- `strategy-writer`: 전략 문서 작성자. OKR·BSC·SWOT 결과를 종합하여 비전·미션 선언문과 전략 실행 로드맵을 작성한다. 경영진 보고용 전략 문서의 최종 형태를 완성한다.
- `swot-specialist`: SWOT 분석 전문가. 조직의 내부 강점·약점과 외부 기회·위협을 체계적으로 분석하고, TOWS 매트릭스를 통한 전략 도출까지 수행한다.

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
- `01_okr_design.md` — OKR 설계서
- `02_bsc_mapping.md` — BSC 매핑표
- `03_swot_analysis.md` — SWOT 분석서
- `04_vision_mission.md` — 비전·미션 선언문
- `05_strategy_roadmap.md` — 전략 실행 로드맵
- `06_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/okr-quality-checker/SKILL.md`
- `.agents/skills/tows-matrix-builder/SKILL.md`
