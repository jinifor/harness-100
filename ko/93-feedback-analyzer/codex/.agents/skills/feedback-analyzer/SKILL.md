---
name: feedback-analyzer
description: >-
  Trigger when: 사용자가 `feedback-analyzer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Feedback Analyzer Harness

고객·직원 피드백 분석 하네스. 데이터 수집부터 감성분석, 주제분류, 트렌드 도출, 인사이트 보고서까지 에이전트 팀이 협업하여 생성한다.

## Specialist Agents

- `data-collector`: 피드백 데이터 수집·정제 전문가. 다양한 채널(설문, 리뷰, CS로그, 인터뷰)의 피드백을 통합하고, 중복 제거, 정규화, 익명화를 수행하여 분석 가능한 데이터셋을 구성한다.
- `insight-writer`: 인사이트 보고서 작성 전문가. 감성분석, 주제분류, 트렌드 결과를 종합하여 경영진/실무자 맞춤 인사이트 보고서를 작성하고 구체적 액션 아이템을 제안한다.
- `sentiment-analyst`: 감성분석 전문가. 피드백 텍스트의 긍정/부정/중립을 판별하고, 감정 강도를 점수화하며, 시간에 따른 감정 변화 추이를 분석한다.
- `topic-classifier`: 주제분류 전문가. 피드백을 의미 기반으로 분류하여 카테고리 체계를 설계하고, 키워드 클러스터링, 태그 맵, 주제별 감정 교차분석을 수행한다.
- `trend-detector`: 트렌드 분석 전문가. 피드백 데이터의 시계열 패턴을 분석하여 상승/하락 트렌드, 이상 탐지, 계절성, 이벤트 상관관계를 도출한다.

## Workflow

1. 사용자 요청, 제약 조건, 기존 자료를 정리한다.
2. 필요하면 `_workspace/00_input.md`에 시작 컨텍스트를 저장한다.
3. 요청 범위에 맞는 specialist를 순차 또는 병렬로 실행하고, 번호가 매겨진 `_workspace/` 산출물로 handoff 한다.
4. 리뷰어 또는 종합 검토 specialist가 있으면 마지막에 전체 결과를 검증한다.
5. 누락된 단계, 한계, 재사용한 입력 파일을 최종 보고에 명시한다.

## 작업 규칙

- source `.claude` 파일은 수정하지 않는다.
- 모든 하네스 산출물은 `_workspace/`에 유지한다.
- 기존 파일이 이미 있으면 적절한 위치에 복사하거나 참조하고 중복 단계를 건너뛸 수 있다.
- 외부 조회나 생성이 실패해도 가능한 범위까지 진행하고 한계를 적는다.

## 산출물

- `00_input.md` — 원본 피드백 데이터 및 분석 요건 정리
- `01_data_collection.md` — 데이터 수집·정제 결과
- `02_sentiment_analysis.md` — 감성분석 결과
- `03_topic_classification.md` — 주제분류 결과
- `04_trend_report.md` — 트렌드 분석 결과
- `05_insight_report.md` — 종합 인사이트 보고서

## 확장 스킬

- `.agents/skills/sentiment-scoring/SKILL.md`
- `.agents/skills/text-analytics-methods/SKILL.md`
