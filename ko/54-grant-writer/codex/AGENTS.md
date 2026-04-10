# Grant Writer Harness Codex 지침

## 목적

- 이 디렉토리는 `Grant Writer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/grant-writer/SKILL.md`
- 전문 agent: `.codex/agents/announcement-analyst.toml`, `.codex/agents/budget-designer.toml`, `.codex/agents/compliance-checker.toml`, `.codex/agents/plan-writer.toml`, `.codex/agents/submission-verifier.toml`
- 확장 스킬: `.agents/skills/budget-rule-engine/SKILL.md`, `.agents/skills/scoring-optimizer/SKILL.md`

## 실행 원칙

- 전체 작업은 `grant-writer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 보조금 및 지원사업 신청을 위한 공고 분석, 사업계획 작성, 예산 편성, 제출 검증까지 에이전트 팀이 협업하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_announcement_analysis.md` — 공고 분석서
- `02_business_plan.md` — 사업계획서
- `03_budget_plan.md` — 예산 편성서
- `04_compliance_report.md` — 규정 준수 보고서
- `05_submission_checklist.md` — 제출 체크리스트
- `06_review_report.md` — 리뷰 보고서
