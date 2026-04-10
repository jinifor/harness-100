# Advertising Campaign Harness Codex 지침

## 목적

- 이 디렉토리는 `Advertising Campaign Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/advertising-campaign/SKILL.md`
- 전문 agent: `.codex/agents/campaign-reviewer.toml`, `.codex/agents/copywriter.toml`, `.codex/agents/creative-director.toml`, `.codex/agents/market-analyst.toml`, `.codex/agents/media-planner.toml`
- 확장 스킬: `.agents/skills/ad-copywriting-formulas/SKILL.md`, `.agents/skills/media-mix-calculator/SKILL.md`

## 실행 원칙

- 전체 작업은 `advertising-campaign` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 광고 캠페인의 타깃분석→카피→크리에이티브→미디어플랜을 에이전트 팀이 협업하여 설계하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_market_analysis.md` — 시장·타깃 분석 보고서
- `02_ad_copy.md` — 광고 카피 세트
- `03_creative_concept.md` — 크리에이티브 컨셉·스토리보드
- `04_media_plan.md` — 미디어 플랜
- `05_review_report.md` — 리뷰 보고서
