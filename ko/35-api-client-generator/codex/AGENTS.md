# API Client Generator Harness Codex 지침

## 목적

- 이 디렉토리는 `API Client Generator Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/api-client-generator/SKILL.md`
- 전문 agent: `.codex/agents/doc-writer.toml`, `.codex/agents/sdk-developer.toml`, `.codex/agents/spec-parser.toml`, `.codex/agents/test-engineer.toml`, `.codex/agents/type-generator.toml`
- 확장 스킬: `.agents/skills/openapi-spec-patterns/SKILL.md`, `.agents/skills/sdk-design-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `api-client-generator` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- API 클라이언트 SDK 생성: 스펙파싱→타입생성→클라이언트코드→테스트→사용문서를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 및 API 스펙 정보
- `01_spec_analysis.md` — API 스펙 분석 결과
- `02_types/` — 생성된 타입 정의 파일
- `03_client/` — SDK 클라이언트 코드
- `04_tests/` — 테스트 코드
- `05_docs/` — 사용 문서
