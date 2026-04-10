# Sustainability Audit Harness Codex 지침

## 목적

- 이 디렉토리는 `Sustainability Audit Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/sustainability-audit/SKILL.md`
- 전문 agent: `.codex/agents/environmental-analyst.toml`, `.codex/agents/esg-reporter.toml`, `.codex/agents/governance-reviewer.toml`, `.codex/agents/improvement-planner.toml`, `.codex/agents/social-assessor.toml`
- 확장 스킬: `.agents/skills/ghg-protocol/SKILL.md`, `.agents/skills/materiality-assessment/SKILL.md`

## 실행 원칙

- 전체 작업은 `sustainability-audit` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- ESG/지속가능성 감사의 환경→사회→거버넌스→보고서→개선계획을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_environmental_assessment.md` — 환경(E) 평가서
- `02_social_assessment.md` — 사회(S) 평가서
- `03_governance_assessment.md` — 거버넌스(G) 평가서
- `04_esg_report.md` — 통합 ESG 보고서
- `05_improvement_plan.md` — 개선 계획서
- `06_review_report.md` — 교차 검증 보고서
