# Patent Drafter Harness Codex 지침

## 목적

- 이 디렉토리는 `Patent Drafter Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/patent-drafter/SKILL.md`
- 전문 agent: `.codex/agents/claim-drafter.toml`, `.codex/agents/drawing-designer.toml`, `.codex/agents/patent-reviewer.toml`, `.codex/agents/prior-art-researcher.toml`, `.codex/agents/specification-writer.toml`
- 확장 스킬: `.agents/skills/claim-drafting-patterns/SKILL.md`, `.agents/skills/prior-art-search-strategy/SKILL.md`

## 실행 원칙

- 전체 작업은 `patent-drafter` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 특허 명세서 작성 — 선행기술조사→청구항→명세서→도면설명을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리 (발명 개요)
- `01_prior_art_report.md` — 선행기술 조사 보고서
- `02_claims.md` — 청구항 세트
- `03_specification.md` — 발명의 상세한 설명
- `04_drawings.md` — 도면 설명서
- `05_review_report.md` — 검증 보고서
