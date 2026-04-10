# API Designer Harness Codex 지침

## 목적

- 이 디렉토리는 `API Designer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/api-designer/SKILL.md`
- 전문 agent: `.codex/agents/api-architect.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/mock-tester.toml`, `.codex/agents/review-auditor.toml`, `.codex/agents/schema-validator.toml`
- 확장 스킬: `.agents/skills/api-error-design/SKILL.md`, `.agents/skills/rest-api-conventions/SKILL.md`

## 실행 원칙

- 전체 작업은 `api-designer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- REST/GraphQL API의 설계·문서화·목업·테스트를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_api_design.md` — API 설계 문서
- `02_schema.yaml` — OpenAPI/GraphQL 스키마 파일
- `03_api_docs.md` — API 개발자 문서
- `04_mock_tests.md` — 목업 서버 설정 및 테스트 결과
- `05_review_report.md` — API 리뷰 보고서
