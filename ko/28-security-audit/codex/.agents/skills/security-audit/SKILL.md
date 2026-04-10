---
name: security-audit
description: >-
  Trigger when: 사용자가 `security-audit` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Security Audit Harness

보안 감사의 취약점스캔→코드분석→침투테스트보고→개선권고를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `audit-reviewer`: 감사 리뷰어(QA). 취약점스캔-코드분석-침투테스트-개선권고 간의 정합성을 교차 검증하고, 위험등급을 조정하며, 최종 감사 보고서를 생성한다.
- `code-analyst`: 코드 보안 분석가. SAST 관점에서 소스코드의 보안 취약점을 정적 분석하고, 시큐어 코딩 위반 사항을 탐지하며, 보안 패턴/안티패턴을 식별한다.
- `pentest-reporter`: 침투 테스트 보고자. 발견된 취약점을 기반으로 실제 공격 시나리오를 설계하고, PoC를 구성하며, 비즈니스 영향을 분석하여 침투 테스트 보고서를 작성한다.
- `security-consultant`: 보안 컨설턴트. 발견된 취약점에 대한 개선 권고, 보안 아키텍처 제안, 프레임워크(ISO 27001, NIST) 매핑, 단기·중기·장기 보안 로드맵을 수립한다.
- `vulnerability-scanner`: 취약점 스캐너. 의존성 취약점(CVE), 인프라 설정 오류, 알려진 보안 취약점을 체계적으로 스캔하고 위험도를 분류하여 보고한다.

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

- `00_input.md` — 감사 범위 및 사용자 입력 정리
- `01_vulnerability_scan.md` — 취약점 스캔 결과
- `02_code_analysis.md` — 코드 보안 분석 보고서
- `03_pentest_report.md` — 침투 테스트 시나리오 보고서
- `04_remediation_plan.md` — 개선 권고 및 로드맵
- `05_audit_report.md` — 최종 감사 보고서

## 확장 스킬

- `.agents/skills/cve-analysis/SKILL.md`
- `.agents/skills/owasp-testing-guide/SKILL.md`
- `.agents/skills/threat-modeling/SKILL.md`
