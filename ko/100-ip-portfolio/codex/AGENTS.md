# IP Portfolio Harness Codex 지침

## 목적

- 이 디렉토리는 `IP Portfolio Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/ip-portfolio/SKILL.md`
- 전문 agent: `.codex/agents/ip-analyst.toml`, `.codex/agents/license-strategist.toml`, `.codex/agents/patent-mapper.toml`, `.codex/agents/protection-advisor.toml`, `.codex/agents/renewal-scheduler.toml`
- 확장 스킬: `.agents/skills/ip-landscape-analysis/SKILL.md`, `.agents/skills/patent-valuation/SKILL.md`

## 실행 원칙

- 전체 작업은 `ip-portfolio` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 지식재산 포트폴리오 관리의 IP현황분석→특허·상표·저작권매핑→갱신일정→라이선스전략→보호전략보고서를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_ip_analysis.md` — IP 현황 분석서
- `02_ip_map.md` — 특허·상표·저작권 매핑
- `03_renewal_schedule.md` — 갱신 일정 관리표
- `04_license_strategy.md` — 라이선스 전략서
- `05_protection_report.md` — 보호 전략 보고서
- `06_review_report.md` — 통합 리뷰 보고서
