---
name: customer-support
description: >-
  Trigger when: 사용자가 `customer-support` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Customer Support Harness

고객지원 시스템 구축: FAQ→응대매뉴얼→에스컬레이션→분석을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `cs-analyst`: CS 분석 전문가. 고객지원 성과 메트릭 체계를 설계하고, VOC(Voice of Customer) 분석 프레임워크, 트렌드 분석, 서비스 개선 제안을 수행한다.
- `cs-reviewer`: 고객지원 시스템 리뷰어(QA). FAQ-응대매뉴얼-에스컬레이션-분석 간의 정합성을 교차 검증하고, 고객 경험 관점에서 시스템 완성도를 평가한다.
- `escalation-manager`: 에스컬레이션 관리 전문가. 고객 문의의 단계별 에스컬레이션 정책, 라우팅 규칙, SLA, 위기 대응 프로토콜을 설계한다.
- `faq-builder`: FAQ 구축 전문가. 고객 문의 패턴을 분석하여 카테고리별 FAQ를 체계적으로 구축하고, 검색 최적화와 셀프서비스율 향상을 위한 구조를 설계한다.
- `response-specialist`: 응대 매뉴얼 전문가. 고객 상황별 응대 스크립트, 톤앤매너 가이드, 감정 대응 프로토콜을 작성한다. 채널별(전화/채팅/이메일) 맞춤 응대 체계를 설계한다.

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
- `01_faq.md` — FAQ 문서
- `02_response_manual.md` — 응대 매뉴얼
- `03_escalation_policy.md` — 에스컬레이션 정책
- `04_cs_analytics.md` — CS 분석 프레임워크
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/csat-analyzer/SKILL.md`
- `.agents/skills/escalation-flowchart/SKILL.md`
