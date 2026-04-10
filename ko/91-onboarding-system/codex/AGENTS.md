# Onboarding System Harness Codex 지침

## 목적

- 이 디렉토리는 `Onboarding System Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/onboarding-system/SKILL.md`
- 전문 agent: `.codex/agents/experience-reviewer.toml`, `.codex/agents/mentor-matcher.toml`, `.codex/agents/milestone-tracker.toml`, `.codex/agents/onboarding-architect.toml`, `.codex/agents/training-builder.toml`
- 확장 스킬: `.agents/skills/buddy-program-guide/SKILL.md`, `.agents/skills/learning-path-design/SKILL.md`

## 실행 원칙

- 전체 작업은 `onboarding-system` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 신규입사자 온보딩: 체크리스트→교육→멘토배정→30-60-90일 계획까지 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_onboarding_checklist.md` — 온보딩 체크리스트 및 일정
- `02_training_program.md` — 교육 프로그램
- `03_mentor_guide.md` — 멘토·버디 배정 가이드
- `04_30_60_90_plan.md` — 30-60-90일 계획
- `05_review_report.md` — 온보딩 경험 검증 보고서
