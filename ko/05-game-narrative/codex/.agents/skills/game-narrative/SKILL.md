---
name: game-narrative
description: >-
  Trigger when: 사용자가 `game-narrative` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Game Narrative Harness

게임 스토리·퀘스트·대사·분기 시나리오를 에이전트 팀이 협업하여 설계하는 하네스.

## Specialist Agents

- `branch-architect`: 게임 분기 설계자. 스토리 분기 구조, 엔딩 변형, 플래그 시스템, 선택의 결과 체계를 설계한다.
- `dialogue-writer`: 게임 대사 작가. NPC 대사, 플레이어 선택지, 감정 연출, 컷신 대사를 캐릭터 성격에 맞게 작성한다.
- `narrative-reviewer`: 게임 내러티브 검증자(QA). 세계관-퀘스트-대사-분기 간의 정합성, 플롯홀, 밸런스를 교차 검증한다.
- `quest-designer`: 게임 퀘스트 디자이너. 메인/사이드 퀘스트를 설계하고, 목표, 단계, 보상, 실패 조건을 구체적으로 정의한다.
- `worldbuilder`: 게임 세계관 설계자. 배경 세계, 세력 관계, 역사, 마법/기술 체계, 지리를 설계하고 내러티브의 토대를 구축한다.

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
- `01_worldbuilding.md` — 세계관 설정 문서
- `02_quest_design.md` — 퀘스트 설계 문서
- `03_dialogue_script.md` — 대사 스크립트
- `04_branch_map.md` — 분기 구조도
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/branching-logic/SKILL.md`
- `.agents/skills/dialogue-systems/SKILL.md`
- `.agents/skills/quest-design-patterns/SKILL.md`
