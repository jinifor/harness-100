# Book Publishing Harness Codex 지침

## 목적

- 이 디렉토리는 `Book Publishing Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/book-publishing/SKILL.md`
- 전문 agent: `.codex/agents/cover-designer.toml`, `.codex/agents/manuscript-editor.toml`, `.codex/agents/metadata-manager.toml`, `.codex/agents/proofreader.toml`, `.codex/agents/publishing-reviewer.toml`
- 확장 스킬: `.agents/skills/book-metadata-seo/SKILL.md`, `.agents/skills/cover-design-psychology/SKILL.md`, `.agents/skills/developmental-editing/SKILL.md`

## 실행 원칙

- 전체 작업은 `book-publishing` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 전자책 출판의 원고편집→표지→목차→메타데이터→배포를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_edited_manuscript.md` — 편집된 원고
- `02_proofread_report.md` — 교정교열 보고서
- `03_cover_concept.md` — 표지 컨셉/이미지
- `04_metadata.md` — 메타데이터/배포 설정
- `05_review_report.md` — 리뷰 보고서
