# Market Research Harness Codex 지침

## 목적

- 이 디렉토리는 `Market Research Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/market-research/SKILL.md`
- 전문 agent: `.codex/agents/competitor-analyst.toml`, `.codex/agents/consumer-analyst.toml`, `.codex/agents/industry-analyst.toml`, `.codex/agents/research-reviewer.toml`, `.codex/agents/trend-analyst.toml`
- 확장 스킬: `.agents/skills/porter-five-forces/SKILL.md`, `.agents/skills/tam-sam-som-calculator/SKILL.md`

## 실행 원칙

- 전체 작업은 `market-research` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 시장 조사의 산업분석→경쟁분석→소비자조사→트렌드→보고서를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_industry_analysis.md` — 산업 분석 보고서
- `02_competitor_analysis.md` — 경쟁 분석 보고서
- `03_consumer_analysis.md` — 소비자 분석 보고서
- `04_trend_analysis.md` — 트렌드 분석 보고서
- `05_review_report.md` — 종합 리서치 보고서
