---
name: crisis-communication
description: >-
  Trigger when: 사용자가 `crisis-communication` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Crisis Communication Harness

위기 상황 발생 시 상황파악→메시지전략→보도자료→Q&A→모니터링까지 에이전트 팀이 협업하여 통합 위기소통 패키지를 생성하는 하네스.

## Specialist Agents

- `media-monitor`: 미디어 모니터링 및 후속 대응 전문가. 언론·SNS 여론 추적, 리스크 감지, 후속 대응 전략, 위기 종료 판단 기준을 수립한다.
- `message-strategist`: 위기 메시지 전략가. 이해관계자별 핵심 메시지, 커뮤니케이션 톤, 채널 전략, 발표 타이밍을 설계한다.
- `press-release-writer`: 보도자료 및 공식 입장문 작성자. 위기 상황에 맞는 보도자료, CEO 서한, 공식 성명을 작성한다.
- `qa-preparer`: 위기 Q&A 준비자. 기자회견, 인터뷰, 내부 질의에 대비한 예상 질문과 답변 가이드, 대변인 브리핑 시트를 작성한다.
- `situation-analyst`: 위기 상황 분석가. 사실관계 파악, 이해관계자 매핑, 위기 등급 판정, 법적·규제적 리스크 식별을 수행한다.

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
- `01_situation_analysis.md` — 상황 분석 보고서
- `02_message_strategy.md` — 메시지 전략서
- `03_press_release.md` — 보도자료/공식 입장문
- `04_qa_briefing.md` — Q&A 브리핑 시트
- `05_monitoring_plan.md` — 모니터링 계획 및 후속 대응 가이드

## 확장 스킬

- `.agents/skills/media-response-templates/SKILL.md`
- `.agents/skills/stakeholder-mapping/SKILL.md`
