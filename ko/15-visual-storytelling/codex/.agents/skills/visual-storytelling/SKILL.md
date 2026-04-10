---
name: visual-storytelling
description: >-
  Trigger when: 사용자가 `visual-storytelling` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Visual Storytelling Harness

비주얼 스토리텔링의 스토리설계→텍스트집필→AI이미지생성→HTML레이아웃→통합편집을 에이전트 팀이 협업하여 제작하는 하네스.

## Specialist Agents

- `editorial-reviewer`: 편집 리뷰어(QA). 스토리-텍스트-이미지-레이아웃 간의 정합성을 교차 검증하고, 내러티브 흐름, 감정 일관성, 시각적 통일감의 품질을 확인한다.
- `essay-writer`: 에세이 작가. 비주얼 스토리텔링의 텍스트 파트를 집필한다. 본문 서술, 캡션, 인용구, 대화 등 장면별로 이미지와 호흡을 맞추는 감정적 문체로 글을 쓴다.
- `image-prompter`: 이미지 프롬프터. Gemini 이미지 생성을 활용하여 비주얼 스토리의 각 장면에 맞는 이미지를 생성한다. 장면 간 시각적 일관성을 유지하는 프롬프트를 설계한다.
- `layout-builder`: 레이아웃 빌더. 텍스트와 이미지를 통합하는 HTML/CSS 기반 비주얼 스토리 페이지를 제작한다. 반응형 디자인, 타이포그래피, 스크롤 경험을 설계한다.
- `story-architect`: 스토리 설계자. 비주얼 스토리텔링의 내러티브 구조, 장면 구성, 시각-텍스트 밸런스를 설계한다. 각 장면이 이미지와 텍스트의 유기적 조합으로 하나의 서사를 이루도록 청사진을 만든다.

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
- `01_story_blueprint.md` — 스토리 블루프린트
- `02_essay_text.md` — 에세이 본문
- `03_image_prompts.md` — 이미지 프롬프트 시트
- `04_layout.html` — HTML 레이아웃
- `05_review_report.md` — 편집 리뷰 보고서
- `images/` — 생성된 이미지 디렉토리

## 확장 스킬

- `.agents/skills/image-prompt-engineering/SKILL.md`
- `.agents/skills/narrative-structure-patterns/SKILL.md`
