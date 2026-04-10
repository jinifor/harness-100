# Changelog Generator Harness Codex 지침

## 목적

- 이 디렉토리는 `Changelog Generator Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/changelog-generator/SKILL.md`
- 전문 agent: `.codex/agents/announcement-writer.toml`, `.codex/agents/change-classifier.toml`, `.codex/agents/commit-analyst.toml`, `.codex/agents/migration-guide-writer.toml`, `.codex/agents/release-note-writer.toml`
- 확장 스킬: `.agents/skills/commit-parser/SKILL.md`, `.agents/skills/semver-analyzer/SKILL.md`

## 실행 원칙

- 전체 작업은 `changelog-generator` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 릴리스 관리의 git이력분석→변경분류→릴리스노트생성→마이그레이션가이드→공지문작성을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_commit_analysis.md` — 커밋 분석 보고서
- `02_change_classification.md` — 변경 분류 결과
- `03_release_notes.md` — 릴리스 노트
- `04_migration_guide.md` — 마이그레이션 가이드
- `05_announcement.md` — 공지문 (블로그/SNS/이메일)
