---
name: side-project-launcher
description: >-
  Trigger when: 사용자가 `side-project-launcher` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Side Project Launcher Harness

사이드프로젝트 기획의 아이디어검증→기술스택선정→MVP스펙→개발로드맵→런칭체크리스트를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `idea-validator`: 아이디어 검증자. 사이드프로젝트 아이디어의 시장성, 경쟁 상황, 차별화 포인트를 분석하고 Go/No-Go 판단을 제공한다.
- `launch-reviewer`: 런칭 리뷰어(QA). 아이디어-기술스택-MVP-로드맵 간의 일관성을 교차 검증하고, 실행 가능성과 리스크를 종합 평가한다.
- `mvp-designer`: MVP 설계자. 핵심 기능을 정의하고, 사용자 플로우와 화면 구성을 설계하며, 구현 가능한 MVP 스펙을 작성한다.
- `roadmap-builder`: 로드맵 작성자. MVP 스펙을 기반으로 개발 일정, 마일스톤, 런칭 전략, 런칭 체크리스트를 수립한다.
- `techstack-analyst`: 기술스택 분석가. 프로젝트 요구사항과 개발자 역량에 맞는 최적 기술스택을 비교·분석하고 추천한다.

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
- `01_idea_validation.md` — 아이디어 검증 보고서
- `02_techstack_recommendation.md` — 기술스택 추천서
- `03_mvp_spec.md` — MVP 스펙 문서
- `04_roadmap_launch.md` — 개발 로드맵 + 런칭 체크리스트
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/market-sizing-calculator/SKILL.md`
- `.agents/skills/techstack-decision-matrix/SKILL.md`
