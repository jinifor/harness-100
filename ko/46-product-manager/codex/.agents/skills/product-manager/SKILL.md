---
name: product-manager
description: >-
  Trigger when: 사용자가 `product-manager` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Product Manager Harness

PM 업무의 로드맵→PRD→유저스토리→스프린트→회고를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `pm-reviewer`: PM 검증자(QA). 로드맵-PRD-유저스토리-스프린트 계획 간의 정합성, 실행 가능성, 누락을 교차 검증한다.
- `prd-writer`: PRD 작성자. 제품 요구사항 정의서를 작성하여 엔지니어링·디자인 팀이 정확히 무엇을 만들어야 하는지 정의한다.
- `sprint-planner`: 스프린트 플래너. 팀 용량 산정, 스프린트 목표 설정, 스토리 배분, 리스크 관리, 회고 템플릿을 설계한다.
- `story-writer`: 유저스토리 작성자. PRD를 기반으로 개발 가능한 유저스토리를 작성하고, 스토리맵, AC(인수기준), 스토리포인트를 정의한다.
- `strategist`: 제품 전략가. 제품 비전, 목표 설정, 로드맵 수립, 우선순위 프레임워크 운영, OKR 정의를 수행한다.

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
- `01_product_roadmap.md` — 제품 로드맵
- `02_prd.md` — 제품 요구사항 정의서
- `03_user_stories.md` — 유저스토리 목록
- `04_sprint_plan.md` — 스프린트 계획
- `05_review_report.md` — PM 검증 보고서

## 확장 스킬

- `.agents/skills/rice-prioritizer/SKILL.md`
- `.agents/skills/story-point-estimator/SKILL.md`
