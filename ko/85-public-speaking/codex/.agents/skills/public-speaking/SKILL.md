---
name: public-speaking
description: >-
  Trigger when: 사용자가 `public-speaking` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Public Speaking Harness

퍼블릭스피킹 종합의 연설문→발표대본→토론준비서→Q&A예상답변→리허설가이드를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `audience-analyst`: 퍼블릭스피킹 청중 분석가. 발표/연설/토론의 대상 청중을 분석하고, 맥락, 기대, 감정 상태, 사전 지식 수준을 파악하여 콘텐츠 전략의 기반을 마련한다.
- `debate-preparer`: 토론 준비 전문가. 발표자의 주장을 강화하고, 예상 반론에 대한 방어 논리를 구축하며, 공격적 교차심문 전략을 수립한다.
- `qa-strategist`: Q&A 전략가. 발표 후 질의응답에 대비하여 예상 질문을 분류하고, 각 질문에 대한 최적 답변 전략과 스크립트를 작성한다.
- `rehearsal-coach`: 리허설 코치 및 교차 검증 전문가(QA). 발표 전달력을 높이는 리허설 가이드를 작성하고, 연설문-토론준비-Q&A 간 정합성을 교차 검증한다.
- `speech-writer`: 퍼블릭스피킹 연설/발표 작가. 청중 분석을 기반으로 설득력 있고 기억에 남는 연설문과 발표 대본을 작성한다. 수사학적 기법과 스토리텔링을 활용한다.

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
- `01_audience_analysis.md` — 청중 분석 보고서
- `02_speech_script.md` — 연설문/발표 대본
- `03_debate_prep.md` — 토론 준비서
- `04_qa_playbook.md` — Q&A 예상 답변집
- `05_rehearsal_guide.md` — 리허설 가이드 및 검증 보고서

## 확장 스킬

- `.agents/skills/audience-engagement/SKILL.md`
- `.agents/skills/rhetoric-patterns/SKILL.md`
