---
name: presentation-designer
description: >-
  Trigger when: 사용자가 `presentation-designer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Presentation Designer Harness

프레젠테이션의 기획→스토리보드→슬라이드→발표노트를 에이전트 팀이 협업하여 제작하는 하네스.

## Specialist Agents

- `deck-reviewer`: 덱 리뷰어(QA). 스토리-정보설계-비주얼-발표노트 간의 일관성을 교차 검증하고, 누락·모순·품질 문제를 발견하여 피드백을 제공한다.
- `info-architect`: 정보 설계자. 데이터를 효과적으로 시각화하는 차트/그래프/다이어그램을 선택하고, 복잡한 정보를 청중이 이해하기 쉬운 형태로 구조화한다.
- `presentation-coach`: 발표 코치. 슬라이드별 발표 노트 작성, 타이밍 배분, 청중 참여 전략, Q&A 예상 답변, 리허설 가이드를 제공한다.
- `storyteller`: 프레젠테이션 스토리텔러. 청중 분석을 기반으로 프레젠테이션의 핵심 메시지를 정의하고, 논리적 흐름과 감정 곡선을 설계한다.
- `visual-designer`: 비주얼 디자이너. 프레젠테이션 슬라이드의 레이아웃, 색상, 타이포그래피, 이미지를 설계하고 마크다운 기반 슬라이드 덱을 제작한다.

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
- `01_story_structure.md` — 스토리 구조·메시지 맵
- `02_info_design.md` — 정보 설계·데이터 시각화 가이드
- `03_slide_deck.md` — 슬라이드 덱 (마크다운 기반)
- `04_speaker_notes.md` — 발표 노트·타이밍·Q&A
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/data-visualization-guide/SKILL.md`
- `.agents/skills/slide-layout-patterns/SKILL.md`
