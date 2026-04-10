---
name: hiring-pipeline
description: >-
  Trigger when: 사용자가 `hiring-pipeline` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Hiring Pipeline Harness

채용 프로세스: JD작성→소싱→스크리닝→면접→평가→오퍼까지 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `interview-designer`: 면접 설계자. 구조화 면접, 역량 기반 질문, 면접관 가이드, 평가표를 설계한다.
- `jd-writer`: JD 작성 전문가. 직무분석, 역량정의, 직무기술서(Job Description), 채용공고를 작성한다.
- `offer-coordinator`: 평가·오퍼 총괄. 최종 후보 평가 종합, 보상 패키지 설계, 오퍼레터 작성, 온보딩 연계를 담당한다.
- `screening-expert`: 스크리닝 전문가. 서류 평가 기준, 사전 과제 설계, 전화/영상 스크리닝 가이드를 작성한다.
- `sourcing-specialist`: 소싱 전문가. 채용 채널 전략, 탤런트풀 구축, 아웃리치 메시지, 채용 브랜딩을 담당한다.

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
- `01_job_description.md` — 직무기술서 및 채용공고
- `02_sourcing_strategy.md` — 소싱 전략
- `03_screening_framework.md` — 스크리닝 프레임워크
- `04_interview_design.md` — 면접 설계서
- `05_evaluation_offer.md` — 최종 평가 및 오퍼 가이드

## 확장 스킬

- `.agents/skills/competency-model/SKILL.md`
- `.agents/skills/interview-scorecard/SKILL.md`
