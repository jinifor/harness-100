# RFP Responder Harness Codex 지침

## 목적

- 이 디렉토리는 `RFP Responder Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/rfp-responder/SKILL.md`
- 전문 agent: `.codex/agents/capability-matcher.toml`, `.codex/agents/pricing-strategist.toml`, `.codex/agents/proposal-reviewer.toml`, `.codex/agents/requirement-analyst.toml`, `.codex/agents/technical-proposer.toml`
- 확장 스킬: `.agents/skills/pricing-calculator/SKILL.md`, `.agents/skills/win-theme-builder/SKILL.md`

## 실행 원칙

- 전체 작업은 `rfp-responder` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- RFI/RFP 응답서 작성을 위한 요구사항 분석, 역량 매칭, 기술 제안, 가격 제안, 차별화 전략까지 에이전트 팀이 협업하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_requirement_analysis.md` — 요구사항 분석서
- `02_capability_matrix.md` — 역량 매칭 매트릭스
- `03_technical_proposal.md` — 기술 제안서
- `04_pricing_proposal.md` — 가격 제안서
- `05_differentiation_strategy.md` — 차별화 전략서
- `06_review_report.md` — 리뷰 보고서
