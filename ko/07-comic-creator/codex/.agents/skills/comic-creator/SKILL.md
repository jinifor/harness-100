---
name: comic-creator
description: >-
  Trigger when: 사용자가 `comic-creator` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Comic Creator Harness

4컷/장편 만화 제작의 콘티→대사→이미지생성→편집을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `comic-editor`: 만화 편집자. 말풍선 배치, 효과음 레이어링, 페이지 레이아웃 최종 구성, 읽기 흐름 최적화를 수행한다. 이미지와 텍스트를 통합하는 최종 편집 지시서를 작성한다.
- `dialogue-writer`: 만화 대사 작가. 캐릭터별 고유 말투로 대사를 작성하고, 효과음(의성어·의태어), 나레이션, 말풍선 지시를 포함한 대사 스크립트를 생성한다.
- `image-generator`: 만화 이미지 생성자. 스토리보드의 콘티를 기반으로 Gemini 이미지 생성을 활용하여 각 패널의 이미지를 제작한다. 캐릭터 일관성과 아트 스타일 통일성을 유지한다.
- `quality-reviewer`: 만화 품질 검증자(QA). 스토리-대사-이미지-편집 간의 일관성을 교차 검증하고, 서사 연속성, 캐릭터 일관성, 읽기 흐름 문제를 발견하여 피드백을 제공한다.
- `storyboarder`: 만화 스토리보더. 시놉시스 구성, 장면 분할, 패널 레이아웃 설계, 콘티 작성을 수행한다. 4컷 만화부터 장편까지 만화 고유의 시각적 서사 구조를 설계한다.

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
- `01_storyboard.md` — 콘티/스토리보드
- `02_dialogue.md` — 대사 스크립트
- `03_image_prompts.md` — 이미지 생성 프롬프트 및 결과
- `04_layout.md` — 페이지 레이아웃/편집 지시서
- `05_review_report.md` — 리뷰 보고서
- `panels/` — 생성된 패널 이미지

## 확장 스킬

- `.agents/skills/character-design-system/SKILL.md`
- `.agents/skills/panel-composition/SKILL.md`
- `.agents/skills/visual-narrative/SKILL.md`
