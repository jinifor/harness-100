# Design System Harness Codex 지침

## 목적

- 이 디렉토리는 `Design System Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/design-system/SKILL.md`
- 전문 agent: `.codex/agents/a11y-auditor.toml`, `.codex/agents/component-developer.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/storybook-builder.toml`, `.codex/agents/token-designer.toml`
- 확장 스킬: `.agents/skills/token-generator/SKILL.md`, `.agents/skills/wcag-checker/SKILL.md`

## 실행 원칙

- 전체 작업은 `design-system` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- UI 디자인 시스템 구축: 디자인토큰→컴포넌트라이브러리→스토리북→접근성검증→문서를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 및 브랜드 정보
- `01_design_tokens/` — 디자인 토큰 정의 파일
- `02_components/` — 컴포넌트 라이브러리 코드
- `03_storybook/` — 스토리북 스토리 및 설정
- `04_a11y_report.md` — 접근성 검증 보고서
- `05_docs/` — 디자인 시스템 문서
