# Brand Identity Harness Codex 지침

## 목적

- 이 디렉토리는 `Brand Identity Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/brand-identity/SKILL.md`
- 전문 agent: `.codex/agents/brand-strategist.toml`, `.codex/agents/copywriter.toml`, `.codex/agents/identity-reviewer.toml`, `.codex/agents/naming-specialist.toml`, `.codex/agents/visual-director.toml`
- 확장 스킬: `.agents/skills/brand-archetype/SKILL.md`, `.agents/skills/color-psychology/SKILL.md`, `.agents/skills/naming-methodology/SKILL.md`

## 실행 원칙

- 전체 작업은 `brand-identity` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 브랜드 아이덴티티의 네이밍→슬로건→톤앤매너→가이드라인을 에이전트 팀이 협업하여 설계하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_brand_strategy.md` — 브랜드 전략 보고서
- `02_naming_candidates.md` — 네이밍 후보
- `03_verbal_identity.md` — 버벌 아이덴티티 (슬로건, 톤앤매너)
- `04_visual_identity.md` — 비주얼 아이덴티티 (컬러, 타이포, 로고)
- `05_review_report.md` — 리뷰 보고서
