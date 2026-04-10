# Audit Report Harness Codex 지침

## 목적

- 이 디렉토리는 `Audit Report Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/audit-report/SKILL.md`
- 전문 agent: `.codex/agents/checklist-builder.toml`, `.codex/agents/findings-analyst.toml`, `.codex/agents/recommendation-writer.toml`, `.codex/agents/scope-designer.toml`, `.codex/agents/tracking-manager.toml`
- 확장 스킬: `.agents/skills/finding-classification/SKILL.md`, `.agents/skills/internal-control-framework/SKILL.md`

## 실행 원칙

- 전체 작업은 `audit-report` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 내부감사 보고서 생성 하네스. 감사 범위 설정부터 체크리스트 작성, 발견사항 정리, 개선 권고, 추적 대장까지 에이전트 팀이 협업하여 생성한다.

## 산출물

- `00_input.md` — 감사 요청 및 배경 정리
- `01_audit_scope.md` — 감사 범위 및 계획
- `02_audit_checklist.md` — 감사 체크리스트
- `03_audit_findings.md` — 발견사항 보고서
- `04_recommendations.md` — 개선 권고안
- `05_tracking_ledger.md` — 이행 추적 대장
- `06_final_report.md` — 종합 감사 보고서
