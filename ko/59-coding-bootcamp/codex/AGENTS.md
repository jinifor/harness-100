# Coding Bootcamp Harness Codex 지침

## 목적

- 이 디렉토리는 `Coding Bootcamp Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/coding-bootcamp/SKILL.md`
- 전문 agent: `.codex/agents/code-reviewer.toml`, `.codex/agents/curriculum-designer.toml`, `.codex/agents/exercise-creator.toml`, `.codex/agents/mentor.toml`
- 확장 스킬: `.agents/skills/code-kata-generator/SKILL.md`, `.agents/skills/tech-interview-prep/SKILL.md`

## 실행 원칙

- 전체 작업은 `coding-bootcamp` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 코딩 교육의 커리큘럼설계→실습과제→코드리뷰→프로젝트→포트폴리오를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_curriculum.md` — 커리큘럼
- `02_exercises/` — 실습과제 디렉토리
- `03_code_review.md` — 코드 리뷰 보고서
- `04_project_spec.md` — 프로젝트 기획서
- `05_portfolio_guide.md` — 포트폴리오 가이드
