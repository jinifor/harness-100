---
name: operations-manual
description: >-
  Trigger when: 사용자가 `operations-manual` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Operations Manual Harness

업무 매뉴얼 자동 생성 하네스. 기존 문서/코드를 분석하여 프로세스 플로차트, 단계별 매뉴얼, FAQ, 교육자료를 에이전트 팀이 협업하여 생성한다.

## Specialist Agents

- `document-analyst`: 기존 문서·코드·위키 분석 전문가. 조직의 현행 업무 프로세스를 추출하고, 암묵지를 명시지로 변환하며, 용어 사전과 프로세스 인벤토리를 작성한다.
- `faq-builder`: FAQ 및 트러블슈팅 가이드 작성 전문가. 업무 수행 중 발생하는 질문과 문제를 예측하여 FAQ, 트러블슈팅 의사결정 트리, 에스컬레이션 가이드를 작성한다.
- `flowchart-designer`: 프로세스 플로차트 설계 전문가. 업무 프로세스를 Mermaid 다이어그램으로 시각화하고, 분기 로직, 병렬 처리, 예외 흐름을 포함한 완전한 프로세스 맵을 작성한다.
- `manual-writer`: 단계별 업무 매뉴얼 작성 전문가. 프로세스 분석 결과를 바탕으로 누구나 따라할 수 있는 절차서, 체크리스트, 스크린샷 가이드를 작성한다.
- `training-producer`: 교육자료 제작 전문가. 매뉴얼 내용을 학습 목표 기반 교육자료로 변환하여 퀴즈, 실습과제, 요약카드, 온보딩 체크리스트를 생성한다.

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

- `00_input.md` — 사용자 입력 및 분석 대상 정리
- `01_document_analysis.md` — 기존 문서/코드 분석 결과
- `02_process_flowcharts.md` — 프로세스 플로차트 (Mermaid)
- `03_step_by_step_manual.md` — 단계별 업무 매뉴얼
- `04_faq_troubleshooting.md` — FAQ 및 트러블슈팅 가이드
- `05_training_materials.md` — 교육자료 패키지
- `06_review_report.md` — 통합 검증 보고서

## 확장 스킬

- `.agents/skills/flowchart-standards/SKILL.md`
- `.agents/skills/knowledge-base-design/SKILL.md`
