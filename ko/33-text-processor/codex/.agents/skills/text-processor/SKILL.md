---
name: text-processor
description: >-
  Trigger when: 사용자가 `text-processor` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Text Processor Harness

텍스트 처리 파이프라인: 대량 텍스트→요약·분류·개체추출·감성분석→구조화 데이터→보고서를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `classifier`: 텍스트 분류 엔진. 주제 분류, 의도 분류, 멀티라벨 태깅, 문서 유형 판별을 수행한다. 분류 체계를 자동 설계하거나 사용자 정의 체계를 적용한다.
- `extractor`: 정보 추출 전문가. 개체명 인식(NER), 키워드 추출, 관계 추출, 자동 요약을 수행하여 비정형 텍스트에서 구조화된 정보를 뽑아낸다.
- `preprocessor`: 텍스트 전처리 전문가. 원시 텍스트의 노이즈 제거, 토큰화, 정규화, 언어 감지, 문장 분리, 인코딩 처리를 수행하여 후속 NLP 작업의 기반을 마련한다.
- `report-writer`: 텍스트 처리 보고서 작성 전문가. 전처리, 분류, 추출, 감성분석 결과를 통합하여 비즈니스 인사이트 중심의 최종 보고서를 작성한다.
- `sentiment-analyzer`: 감성 분석 전문가. 텍스트의 극성(긍정/부정/중립), 감정(기쁨/분노/슬픔 등), 측면별 감성(제품-기능별), 의견 마이닝을 수행한다.

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

- `00_input.md` — 사용자 입력 및 텍스트 소스 정리
- `01_preprocessing_result.md` — 전처리 결과 및 텍스트 통계
- `02_classification_result.md` — 분류 결과
- `03_extraction_result.md` — 추출 결과 (개체, 키워드, 요약)
- `04_sentiment_result.md` — 감성 분석 결과
- `05_final_report.md` — 최종 통합 보고서
- `structured_data/` — JSON/CSV 구조화 데이터

## 확장 스킬

- `.agents/skills/nlp-preprocessing-toolkit/SKILL.md`
- `.agents/skills/sentiment-lexicon-builder/SKILL.md`
