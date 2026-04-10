# Text Processor Harness Codex 지침

## 목적

- 이 디렉토리는 `Text Processor Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/text-processor/SKILL.md`
- 전문 agent: `.codex/agents/classifier.toml`, `.codex/agents/extractor.toml`, `.codex/agents/preprocessor.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/sentiment-analyzer.toml`
- 확장 스킬: `.agents/skills/nlp-preprocessing-toolkit/SKILL.md`, `.agents/skills/sentiment-lexicon-builder/SKILL.md`

## 실행 원칙

- 전체 작업은 `text-processor` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 텍스트 처리 파이프라인: 대량 텍스트→요약·분류·개체추출·감성분석→구조화 데이터→보고서를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 및 텍스트 소스 정리
- `01_preprocessing_result.md` — 전처리 결과 및 텍스트 통계
- `02_classification_result.md` — 분류 결과
- `03_extraction_result.md` — 추출 결과 (개체, 키워드, 요약)
- `04_sentiment_result.md` — 감성 분석 결과
- `05_final_report.md` — 최종 통합 보고서
- `structured_data/` — JSON/CSV 구조화 데이터
