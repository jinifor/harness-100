# Legal Research Harness Codex 지침

## 목적

- 이 디렉토리는 `Legal Research Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/legal-research/SKILL.md`
- 전문 agent: `.codex/agents/case-searcher.toml`, `.codex/agents/legal-analyst.toml`, `.codex/agents/opinion-writer.toml`, `.codex/agents/strategy-advisor.toml`
- 확장 스킬: `.agents/skills/case-analysis-framework/SKILL.md`, `.agents/skills/legal-writing-methodology/SKILL.md`

## 실행 원칙

- 전체 작업은 `legal-research` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 법률 리서치 — 판례검색→법리분석→의견서→전략수립을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리 (법률 이슈)
- `01_case_search.md` — 판례 검색 보고서
- `02_legal_analysis.md` — 법리 분석 보고서
- `03_legal_opinion.md` — 법률 의견서
- `04_legal_strategy.md` — 전략 수립 보고서
