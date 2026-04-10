# Procurement Docs Harness Codex 지침

## 목적

- 이 디렉토리는 `Procurement Docs Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/procurement-docs/SKILL.md`
- 전문 agent: `.codex/agents/acceptance-builder.toml`, `.codex/agents/contract-reviewer.toml`, `.codex/agents/evaluation-designer.toml`, `.codex/agents/requirements-definer.toml`, `.codex/agents/vendor-comparator.toml`
- 확장 스킬: `.agents/skills/contract-checklist/SKILL.md`, `.agents/skills/vendor-scoring/SKILL.md`

## 실행 원칙

- 전체 작업은 `procurement-docs` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 구매 문서세트 생성 하네스. 요구사항 정의부터 벤더 비교표, 평가 기준표, 계약 조건 검토, 검수 기준서까지 에이전트 팀이 협업하여 생성한다.

## 산출물

- `00_input.md` — 구매 요청 및 배경 정리
- `01_requirements_spec.md` — 구매 요구사항 정의서
- `02_vendor_comparison.md` — 벤더 비교 분석표
- `03_evaluation_criteria.md` — 평가 기준표
- `04_contract_review.md` — 계약 조건 검토서
- `05_acceptance_criteria.md` — 검수 기준서
- `06_procurement_summary.md` — 구매 종합 보고서
