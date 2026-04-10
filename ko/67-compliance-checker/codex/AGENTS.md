# Compliance Checker Harness Codex 지침

## 목적

- 이 디렉토리는 `Compliance Checker Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/compliance-checker/SKILL.md`
- 전문 agent: `.codex/agents/gap-analyst.toml`, `.codex/agents/law-mapper.toml`, `.codex/agents/remediation-planner.toml`, `.codex/agents/status-auditor.toml`
- 확장 스킬: `.agents/skills/audit-checklist-engine/SKILL.md`, `.agents/skills/regulation-knowledge-base/SKILL.md`

## 실행 원칙

- 전체 작업은 `compliance-checker` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 규정 준수 검증 — 법률매핑→현황진단→갭분석→개선계획을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_law_mapping.md` — 법률 매핑 보고서
- `02_status_audit.md` — 현황 진단 보고서
- `03_gap_analysis.md` — 갭 분석 보고서
- `04_remediation_plan.md` — 개선 계획서
