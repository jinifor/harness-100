# Wedding Planner Harness Codex 지침

## 목적

- 이 디렉토리는 `Wedding Planner Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/wedding-planner/SKILL.md`
- 전문 agent: `.codex/agents/budget-controller.toml`, `.codex/agents/checklist-builder.toml`, `.codex/agents/timeline-designer.toml`, `.codex/agents/vendor-analyst.toml`, `.codex/agents/wedding-reviewer.toml`
- 확장 스킬: `.agents/skills/vendor-negotiation-guide/SKILL.md`, `.agents/skills/wedding-budget-optimizer/SKILL.md`

## 실행 원칙

- 전체 작업은 `wedding-planner` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 결혼 준비 종합의 타임라인설계→예산관리표→업체비교표→체크리스트→청첩장문구를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_timeline.md` — 결혼 준비 타임라인
- `02_budget.md` — 예산 관리표
- `03_vendor_comparison.md` — 업체 비교표
- `04_checklist_invitation.md` — 체크리스트 + 청첩장 문구
- `05_review_report.md` — 리뷰 보고서
