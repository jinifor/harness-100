---
name: meeting-strategist
description: >-
  Trigger when: 사용자가 `meeting-strategist` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Meeting Strategist Harness

회의 전략 문서의 안건구조설계→배경자료조사→의사결정프레임워크→회의록템플릿→팔로업플랜을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `agenda-architect`: 회의 안건 설계자. 회의 목적을 명확히 정의하고, 안건 구조, 시간 배분, 참석자 역할, 진행 방식을 설계한다.
- `background-researcher`: 회의 배경 조사원. 각 안건에 필요한 데이터, 사례, 이해관계자 분석, 이전 회의 결정사항을 조사하여 참석자의 판단을 지원하는 브리프를 작성한다.
- `followup-planner`: 회의 팔로업 플래너 및 교차 검증 전문가(QA). 회의 후 실행 계획을 수립하고, 안건-배경-프레임워크-템플릿 간 정합성을 교차 검증한다.
- `framework-designer`: 의사결정 프레임워크 설계자. 회의에서 다룰 의사결정 안건에 대해 판단 기준, 옵션 비교 매트릭스, 리스크 평가, 합의 도출 방법을 설계한다.
- `template-builder`: 회의 문서 템플릿 빌더. 회의록, 결정사항 기록지, 투표 양식, 보고서 양식 등 회의 운영에 필요한 모든 문서 템플릿을 생성한다.

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
- `01_agenda_design.md` — 안건 구조 설계서
- `02_background_brief.md` — 배경 자료 브리프
- `03_decision_framework.md` — 의사결정 프레임워크
- `04_meeting_templates.md` — 회의록 및 보고 템플릿
- `05_followup_plan.md` — 팔로업 플랜 및 검증 보고서

## 확장 스킬

- `.agents/skills/decision-frameworks/SKILL.md`
- `.agents/skills/facilitation-techniques/SKILL.md`
