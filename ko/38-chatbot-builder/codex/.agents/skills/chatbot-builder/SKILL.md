---
name: chatbot-builder
description: >-
  Trigger when: 사용자가 `chatbot-builder` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Chatbot Builder Harness

챗봇 구축의 의도분석→대화설계→NLU→통합→테스트를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `conversation-designer`: 대화 설계자. 챗봇의 대화 시나리오, 플로우차트, 폴백 전략, 멀티턴 대화 관리를 설계한다. 사용자 여정 전체를 커버하는 대화 구조를 구축한다.
- `dialog-tester`: 대화 테스터. 챗봇의 대화 시나리오 테스트, 엣지케이스 검증, 페르소나 일관성 확인, 성능 측정을 수행한다. 품질 게이트 역할을 담당한다.
- `integration-engineer`: 통합 엔지니어. 챗봇을 메시징 채널(Slack, 카카오톡, 웹)에 연동하고, 외부 API/DB와의 통합을 구현한다. 배포 및 인프라를 담당한다.
- `nlu-developer`: NLU 개발자. 자연어 이해 파이프라인을 설계·구현한다. 의도분류 모델, 엔티티 추출, 컨텍스트 관리, 프롬프트 엔지니어링을 담당한다.
- `persona-architect`: 챗봇 페르소나 설계자. 봇의 성격, 말투, 톤앤매너, 브랜드 정합성을 정의한다. 사용자 경험의 일관성을 위한 페르소나 가이드라인을 수립한다.

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
- `01_persona_spec.md` — 봇 페르소나 명세
- `02_conversation_design.md` — 대화 설계서
- `03_nlu_config.md` — NLU 설정 및 학습 데이터
- `04_integration_spec.md` — 통합 명세서
- `05_test_report.md` — 테스트 보고서
- `src/` — 챗봇 소스코드

## 확장 스킬

- `.agents/skills/conversation-flow-validator/SKILL.md`
- `.agents/skills/intent-taxonomy-builder/SKILL.md`
