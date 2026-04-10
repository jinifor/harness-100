# CLI Tool Builder Harness Codex 지침

## 목적

- 이 디렉토리는 `CLI Tool Builder Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/cli-tool-builder/SKILL.md`
- 전문 agent: `.codex/agents/command-designer.toml`, `.codex/agents/core-developer.toml`, `.codex/agents/docs-writer.toml`, `.codex/agents/release-engineer.toml`, `.codex/agents/test-engineer.toml`
- 확장 스킬: `.agents/skills/arg-parser-generator/SKILL.md`, `.agents/skills/ux-linter/SKILL.md`

## 실행 원칙

- 전체 작업은 `cli-tool-builder` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- CLI 도구 개발의 명령설계→파서→핸들러→테스트→문서→배포설정을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_command_design.md` — 명령 체계 설계서
- `02_core_implementation.md` — 코어 구현 문서
- `03_test_suite.md` — 테스트 스위트
- `04_documentation.md` — 사용자 문서
- `05_release_config.md` — 릴리스 설정
- `src/` — CLI 소스코드
