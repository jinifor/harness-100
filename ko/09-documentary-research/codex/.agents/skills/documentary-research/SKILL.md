---
name: documentary-research
description: >-
  Trigger when: 사용자가 `documentary-research` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Documentary Research Harness

다큐멘터리 리서치·구성안·인터뷰질문·내레이션 대본을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `fact-checker`: 다큐멘터리 팩트체커(QA). 리서치-구성안-인터뷰-내레이션 간의 사실 정확성과 정합성을 교차 검증하고, 출처 확인, 논리 오류, 편향성을 점검하여 피드백을 제공한다.
- `interviewer`: 다큐멘터리 인터뷰어. 인터뷰 대상별 맞춤 질문을 설계하고, 인터뷰 전략, 순서, 후속 질문을 포함한 인터뷰 가이드를 작성한다.
- `narrator`: 다큐멘터리 내레이터. 구성안에 따라 내레이션 대본을 작성한다. 씬별 톤, 리듬, 감정 전환, 팩트 전달을 포함한 완성된 내레이션 스크립트를 생성한다.
- `researcher`: 다큐멘터리 리서처. 주제에 대한 심층 자료조사, 통계 수집, 전문가 목록 작성, 역사적 맥락 분석, 참고문헌 정리를 수행한다.
- `story-architect`: 다큐멘터리 구성작가. 리서치 결과를 3막 구성안으로 변환하고, 씬 분할, 서사 아크, 감정 곡선, 시퀀스 구조를 설계한다.

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
- `01_research_brief.md` — 리서치 브리프
- `02_structure.md` — 구성안/구조 설계
- `03_interview_guide.md` — 인터뷰 가이드
- `04_narration_script.md` — 내레이션 대본
- `05_review_report.md` — 팩트체크/리뷰 보고서

## 확장 스킬

- `.agents/skills/interview-design/SKILL.md`
- `.agents/skills/investigative-research/SKILL.md`
- `.agents/skills/narrative-structure/SKILL.md`
