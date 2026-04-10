# Technical Writer Harness Codex 지침

## 목적

- 이 디렉토리는 `Technical Writer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/technical-writer/SKILL.md`
- 전문 agent: `.codex/agents/diagram-maker.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/info-architect.toml`, `.codex/agents/tech-reviewer.toml`, `.codex/agents/version-controller.toml`
- 확장 스킬: `.agents/skills/api-doc-standards/SKILL.md`, `.agents/skills/code-example-patterns/SKILL.md`, `.agents/skills/diagram-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `technical-writer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 기술 문서 작성의 구조설계→집필→다이어그램→리뷰→버전관리를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_doc_structure.md` — 문서 구조 설계서
- `02_doc_draft.md` — 문서 본문 초안
- `03_diagrams.md` — 다이어그램 모음
- `04_review_report.md` — 기술 리뷰 보고서
- `05_version_meta.md` — 버전 관리 메타데이터
