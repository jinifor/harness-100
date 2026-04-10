# Startup Launcher Harness Codex 지침

## 목적

- 이 디렉토리는 `Startup Launcher Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/startup-launcher/SKILL.md`
- 전문 agent: `.codex/agents/business-modeler.toml`, `.codex/agents/launch-reviewer.toml`, `.codex/agents/market-analyst.toml`, `.codex/agents/mvp-architect.toml`, `.codex/agents/pitch-creator.toml`
- 확장 스킬: `.agents/skills/pitch-deck-framework/SKILL.md`, `.agents/skills/unit-economics-calculator/SKILL.md`

## 실행 원칙

- 전체 작업은 `startup-launcher` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 스타트업 런칭의 아이디어 검증→비즈니스 모델→MVP→피칭→투자 유치를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_market_validation.md` — 시장 검증 보고서
- `02_business_model.md` — 비즈니스 모델 설계서
- `03_mvp_blueprint.md` — MVP 설계도
- `04_pitch_deck.md` — 피치덱
- `05_review_report.md` — 런칭 검증 보고서
