---
name: ip-portfolio
description: >-
  Trigger when: 사용자가 `ip-portfolio` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# IP Portfolio Harness

지식재산 포트폴리오 관리의 IP현황분석→특허·상표·저작권매핑→갱신일정→라이선스전략→보호전략보고서를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `ip-analyst`: IP 분석가. 조직의 지식재산 포트폴리오 현황을 파악하고, IP 자산의 가치를 평가하며, 전략적 포트폴리오 맵을 작성한다.
- `license-strategist`: IP 라이선스 전략가. IP 자산의 수익화 전략, 크로스라이선스, 기술이전, 오픈소스 전략을 수립하고 라이선스 계약 조건을 설계한다.
- `patent-mapper`: 특허·상표·저작권 매퍼. IP 자산을 체계적으로 분류하고, 등록 현황, 권리 범위, 패밀리 관계를 매핑하여 관리 가능한 IP 맵을 생성한다.
- `protection-advisor`: IP 보호 전략 수립자. 침해 모니터링, 방어 전략, 분쟁 대응, 보호 강화 방안을 수립하고 종합 보호 전략 보고서를 작성한다.
- `renewal-scheduler`: IP 갱신 일정 관리자. 특허 연차료, 상표 갱신, 디자인 갱신의 기한을 관리하고, 비용을 산정하며, 유지/포기 의사결정을 지원한다.

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
- `01_ip_analysis.md` — IP 현황 분석서
- `02_ip_map.md` — 특허·상표·저작권 매핑
- `03_renewal_schedule.md` — 갱신 일정 관리표
- `04_license_strategy.md` — 라이선스 전략서
- `05_protection_report.md` — 보호 전략 보고서
- `06_review_report.md` — 통합 리뷰 보고서

## 확장 스킬

- `.agents/skills/ip-landscape-analysis/SKILL.md`
- `.agents/skills/patent-valuation/SKILL.md`
