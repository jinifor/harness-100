# Gov Funding Plan Harness Codex 지침

## 목적

- 이 디렉토리는 `Gov Funding Plan Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/gov-funding-plan/SKILL.md`
- 전문 agent: `.codex/agents/announcement-analyst.toml`, `.codex/agents/biz-writer.toml`, `.codex/agents/budget-planner.toml`, `.codex/agents/submission-reviewer.toml`, `.codex/agents/tech-writer.toml`
- 확장 스킬: `.agents/skills/budget-standard-checker/SKILL.md`, `.agents/skills/scoring-optimizer/SKILL.md`

## 실행 원칙

- 전체 작업은 `gov-funding-plan` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 정부지원사업 사업계획서의 공고요건분석→기술성·사업성작성→예산편성→증빙준비→제출검증을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_announcement_analysis.md` — 공고 요건 분석서
- `02_tech_proposal.md` — 기술성 파트
- `03_biz_proposal.md` — 사업성 파트
- `04_budget_plan.md` — 예산 편성서
- `05_review_report.md` — 제출 검증 보고서
