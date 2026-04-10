---
name: ml-experiment
description: >-
  Trigger when: 사용자가 `ml-experiment` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# ML Experiment Harness

ML 실험 관리의 데이터준비→모델설계→학습→평가→배포를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `data-engineer`: ML 데이터 엔지니어. 데이터 수집, 탐색적 분석(EDA), 전처리, 피처 엔지니어링, 데이터 분할, 데이터 버전 관리를 수행하여 학습에 최적화된 데이터셋을 구축한다.
- `evaluation-analyst`: 평가 분석가. 모델 성능 메트릭 분석, 오류 분석, 편향 검증, 해석 가능성(XAI), 배포 준비도를 평가하고, A/B 테스트 설계를 수행한다.
- `experiment-reviewer`: 실험 리뷰어(QA). 데이터-모델-학습-평가 간의 정합성을 교차 검증하고, 실험의 과학적 엄밀성과 재현 가능성을 평가하며, 최종 보고서를 생성한다.
- `model-designer`: 모델 설계자. ML/DL 모델 아키텍처 설계, 하이퍼파라미터 공간 정의, 손실 함수 선정, 정규화 전략을 수립하고 모델 코드를 구현한다.
- `training-manager`: 학습 관리자. 실험 추적(MLflow/W&B), GPU 리소스 관리, 학습 루프 구현, 체크포인트 관리, 재현성 보장, 하이퍼파라미터 튜닝을 수행한다.

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

- `00_input.md` — 사용자 입력 정리
- `01_data_preparation.md` — 데이터 준비 계획 및 파이프라인
- `02_model_design.md` — 모델 아키텍처 설계
- `03_training_config.md` — 학습 설정 및 실험 추적
- `04_evaluation_report.md` — 평가 보고서
- `05_review_report.md` — 실험 리뷰 보고서
- `experiment_code/` — 실험 구현 코드

## 확장 스킬

- `.agents/skills/experiment-tracking-setup/SKILL.md`
- `.agents/skills/feature-engineering-cookbook/SKILL.md`
- `.agents/skills/model-selection-guide/SKILL.md`
