# Translation & Localization Harness Codex 지침

## 목적

- 이 디렉토리는 `Translation & Localization Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/translation-localization/SKILL.md`
- 전문 agent: `.codex/agents/localizer.toml`, `.codex/agents/quality-reviewer.toml`, `.codex/agents/style-harmonizer.toml`, `.codex/agents/terminology-manager.toml`, `.codex/agents/translator.toml`
- 확장 스킬: `.agents/skills/cultural-adaptation-guide/SKILL.md`, `.agents/skills/translation-quality-mqm/SKILL.md`

## 실행 원칙

- 전체 작업은 `translation-localization` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 다국어 번역·현지화·문화적응·용어관리를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_source_analysis.md` — 원문 분석·번역 전략
- `02_terminology.md` — 용어집
- `03_translation.md` — 번역문
- `04_localization.md` — 현지화 적용 결과
- `05_review_report.md` — 품질 검증 보고서
