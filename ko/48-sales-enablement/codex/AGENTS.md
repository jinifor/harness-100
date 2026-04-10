# Sales Enablement Harness Codex 지침

## 목적

- 이 디렉토리는 `Sales Enablement Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/sales-enablement/SKILL.md`
- 전문 agent: `.codex/agents/customer-analyst.toml`, `.codex/agents/followup-manager.toml`, `.codex/agents/presenter.toml`, `.codex/agents/proposal-writer.toml`, `.codex/agents/sales-reviewer.toml`
- 확장 스킬: `.agents/skills/objection-handler/SKILL.md`, `.agents/skills/roi-calculator/SKILL.md`

## 실행 원칙

- 전체 작업은 `sales-enablement` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 영업 지원 파이프라인: 고객분석→제안서→프레젠테이션→팔로업을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_customer_analysis.md` — 고객 분석서
- `02_proposal.md` — 제안서
- `03_presentation.md` — 프레젠테이션 구성안
- `04_followup_plan.md` — 팔로업 계획서
- `05_review_report.md` — 리뷰 보고서
