# Strategy Framework Harness Codex 지침

## 목적

- 이 디렉토리는 `Strategy Framework Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/strategy-framework/SKILL.md`
- 전문 agent: `.codex/agents/bsc-analyst.toml`, `.codex/agents/okr-designer.toml`, `.codex/agents/strategy-reviewer.toml`, `.codex/agents/strategy-writer.toml`, `.codex/agents/swot-specialist.toml`
- 확장 스킬: `.agents/skills/okr-quality-checker/SKILL.md`, `.agents/skills/tows-matrix-builder/SKILL.md`

## 실행 원칙

- 전체 작업은 `strategy-framework` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 조직의 전략 프레임워크를 OKR설계→BSC매핑→SWOT분석→비전·미션선언문→전략실행로드맵 순으로 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_okr_design.md` — OKR 설계서
- `02_bsc_mapping.md` — BSC 매핑표
- `03_swot_analysis.md` — SWOT 분석서
- `04_vision_mission.md` — 비전·미션 선언문
- `05_strategy_roadmap.md` — 전략 실행 로드맵
- `06_review_report.md` — 리뷰 보고서
