# Fullstack Web App Harness Codex 지침

## 목적

- 이 디렉토리는 `Fullstack Web App Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/fullstack-webapp/SKILL.md`
- 전문 agent: `.codex/agents/architect.toml`, `.codex/agents/backend-dev.toml`, `.codex/agents/devops-engineer.toml`, `.codex/agents/frontend-dev.toml`, `.codex/agents/qa-engineer.toml`
- 확장 스킬: `.agents/skills/api-security-checklist/SKILL.md`, `.agents/skills/component-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `fullstack-webapp` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 풀스택 웹앱의 요구사항→설계→프론트엔드→백엔드→테스트→배포를 에이전트 팀이 협업하여 개발하는 하네스.

## 산출물

- `_workspace/00_input.md` — 사용자 입력 정리
- `_workspace/01_architecture.md` — 아키텍처 설계 문서
- `_workspace/02_api_spec.md` — API 명세
- `_workspace/03_db_schema.md` — DB 스키마
- `_workspace/04_test_plan.md` — 테스트 계획
- `_workspace/05_deploy_guide.md` — 배포 가이드
- `_workspace/06_review_report.md` — 리뷰 보고서
- `src/` — 소스 코드 (프론트엔드 + 백엔드)
