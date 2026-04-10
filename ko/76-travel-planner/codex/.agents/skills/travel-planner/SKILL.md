---
name: travel-planner
description: >-
  Trigger when: 사용자가 `travel-planner` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Travel Planner Harness

여행 계획의 목적지분석→일정→숙소→예산→현지정보를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `budget-manager`: 여행 예산 관리 전문가. 항공·숙소·식비·교통·관광·쇼핑 등 전체 여행 예산을 산출하고, 예산 범위 내 최적 배분을 설계한다.
- `destination-analyst`: 목적지 분석 전문가. 여행지의 관광자원, 최적 방문 시기, 비자·입국 요건, 안전 정보를 종합 분석하여 여행 설계의 기초를 마련한다.
- `itinerary-designer`: 일정 설계 전문가. 목적지 분석을 기반으로 효율적인 동선의 일별 상세 일정을 설계하고, 시간 배분과 이동 경로를 최적화한다.
- `local-guide`: 현지 정보 가이드. 교통 이용법, 맛집, 문화 에티켓, 유용한 앱, 긴급 연락처 등 현지에서 필요한 실용 정보를 종합 제공한다.

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
- `01_destination_analysis.md` — 목적지 분석 보고서
- `02_itinerary.md` — 일정표
- `03_accommodation.md` — 숙소 가이드
- `04_budget.md` — 예산 계획서
- `05_local_guide.md` — 현지 정보 가이드

## 확장 스킬

- `.agents/skills/budget-calculator/SKILL.md`
- `.agents/skills/route-optimizer/SKILL.md`
