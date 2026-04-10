---
name: privacy-engineer
description: >-
  Trigger when: 사용자가 `privacy-engineer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Privacy Engineer Harness

개인정보보호 엔지니어링 — GDPR/PIPA 분석→PIA→동의서→프로세스설계를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `consent-designer`: 동의서 작성자. 법률 분석과 PIA 결과를 기반으로 개인정보 수집·이용 동의서, 개인정보 처리방침, 고지사항을 설계·작성한다.
- `pia-assessor`: PIA 수행자. 개인정보 영향평가(Privacy Impact Assessment)를 체계적으로 수행하고, 위험도를 산정하며, 보호 조치를 권고한다.
- `privacy-law-analyst`: 개인정보보호 법률 분석가. GDPR, 개인정보보호법(PIPA), 정보통신망법 등 적용 법률을 분석하고, 서비스 유형별 의무사항을 매핑한다.
- `process-architect`: 프로세스 설계자. 개인정보 처리의 전체 라이프사이클을 설계하고, 기술적·관리적 보호조치를 구체화하며, 운영 프로세스를 정의한다.

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
- `01_privacy_law_analysis.md` — 법률 분석 보고서
- `02_pia_report.md` — 개인정보 영향평가 보고서
- `03_consent_documents.md` — 동의서·고지사항 세트
- `04_process_design.md` — 개인정보 처리 프로세스 설계서

## 확장 스킬

- `.agents/skills/data-flow-mapper/SKILL.md`
- `.agents/skills/gdpr-pipa-cross-reference/SKILL.md`
