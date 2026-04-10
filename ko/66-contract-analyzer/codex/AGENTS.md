# Contract Analyzer Harness Codex 지침

## 목적

- 이 디렉토리는 `Contract Analyzer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/contract-analyzer/SKILL.md`
- 전문 agent: `.codex/agents/clause-analyst.toml`, `.codex/agents/clause-drafter.toml`, `.codex/agents/comparison-reviewer.toml`, `.codex/agents/contract-coordinator.toml`, `.codex/agents/risk-assessor.toml`
- 확장 스킬: `.agents/skills/clause-risk-database/SKILL.md`, `.agents/skills/negotiation-playbook/SKILL.md`

## 실행 원칙

- 전체 작업은 `contract-analyzer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 계약서 분석·작성·검토·위험 평가를 에이전트 팀이 협업하여 수행하는 하네스. 조항 분석부터 리스크 평가, 비교 검토, 수정 제안까지 계약 관리 전 과정을 체계적으로 처리한다.

## 산출물

- `00_input.md` — 사용자 입력 정리 (계약 유형, 당사자, 요구사항)
- `01_clause_analysis.md` — 조항 분석서
- `02_draft_clauses.md` — 조항 작성/수정안
- `03_risk_assessment.md` — 리스크 평가 보고서
- `04_comparison_report.md` — 비교 검토 보고서
- `05_final_opinion.md` — 종합 법률 의견서
