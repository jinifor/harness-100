# Feedback Analyzer Harness Codex 지침

## 목적

- 이 디렉토리는 `Feedback Analyzer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/feedback-analyzer/SKILL.md`
- 전문 agent: `.codex/agents/data-collector.toml`, `.codex/agents/insight-writer.toml`, `.codex/agents/sentiment-analyst.toml`, `.codex/agents/topic-classifier.toml`, `.codex/agents/trend-detector.toml`
- 확장 스킬: `.agents/skills/sentiment-scoring/SKILL.md`, `.agents/skills/text-analytics-methods/SKILL.md`

## 실행 원칙

- 전체 작업은 `feedback-analyzer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 고객·직원 피드백 분석 하네스. 데이터 수집부터 감성분석, 주제분류, 트렌드 도출, 인사이트 보고서까지 에이전트 팀이 협업하여 생성한다.

## 산출물

- `00_input.md` — 원본 피드백 데이터 및 분석 요건 정리
- `01_data_collection.md` — 데이터 수집·정제 결과
- `02_sentiment_analysis.md` — 감성분석 결과
- `03_topic_classification.md` — 주제분류 결과
- `04_trend_report.md` — 트렌드 분석 결과
- `05_insight_report.md` — 종합 인사이트 보고서
