---
name: service-legal-docs
description: >-
  Trigger when: 사용자가 `service-legal-docs` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Service Legal Docs Harness

서비스 법무문서 세트 — 이용약관→개인정보처리방침→쿠키정책→환불정책→저작권고지 일체를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `consistency-reviewer`: 정합성 검증자. 이용약관·개인정보처리방침·쿠키정책·환불정책·저작권고지 간의 일관성을 교차 검증하고, 법적 정합성을 최종 확인한다.
- `consumer-analyst`: 소비자보호 분석가. 환불정책과 저작권고지를 작성하고, 전자상거래법·소비자보호법 요건을 반영한다.
- `privacy-specialist`: 개인정보 전문가. 개인정보처리방침과 쿠키정책을 법적 요건에 맞게 작성하고, 동의 체계를 설계한다.
- `tos-specialist`: 약관 전문가. 서비스 이용약관을 작성하고, 불공정약관 조항을 방지하며, 서비스 제공자의 권리와 책임을 적절히 설계한다.

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
- `01_terms_of_service.md` — 이용약관
- `02_privacy_policy.md` — 개인정보처리방침
- `03_cookie_policy.md` — 쿠키 정책
- `04_refund_policy.md` — 환불 정책
- `05_copyright_notice.md` — 저작권 고지
- `06_review_report.md` — 정합성 검증 보고서

## 확장 스킬

- `.agents/skills/cross-document-linker/SKILL.md`
- `.agents/skills/unfair-terms-detector/SKILL.md`
