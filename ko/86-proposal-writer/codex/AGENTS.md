# Proposal Writer Harness Codex 지침

## 목적

- 이 디렉토리는 `Proposal Writer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/proposal-writer/SKILL.md`
- 전문 agent: `.codex/agents/client-analyst.toml`, `.codex/agents/differentiator.toml`, `.codex/agents/pricing-strategist.toml`, `.codex/agents/proposal-designer.toml`, `.codex/agents/solution-architect.toml`
- 확장 스킬: `.agents/skills/roi-calculator/SKILL.md`, `.agents/skills/win-theme-builder/SKILL.md`

## 실행 원칙

- 전체 작업은 `proposal-writer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 제안서의 고객분석→솔루션설계→가격→차별화→디자인을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_client_analysis.md` — 고객 분석 보고서
- `02_solution_design.md` — 솔루션 설계서
- `03_pricing_model.md` — 가격 전략서
- `04_differentiation.md` — 차별화 전략서
- `05_final_proposal.md` — 최종 제안서 및 검증 보고서
