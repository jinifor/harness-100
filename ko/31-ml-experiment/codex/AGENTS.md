# ML Experiment Harness Codex 지침

## 목적

- 이 디렉토리는 `ML Experiment Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/ml-experiment/SKILL.md`
- 전문 agent: `.codex/agents/data-engineer.toml`, `.codex/agents/evaluation-analyst.toml`, `.codex/agents/experiment-reviewer.toml`, `.codex/agents/model-designer.toml`, `.codex/agents/training-manager.toml`
- 확장 스킬: `.agents/skills/experiment-tracking-setup/SKILL.md`, `.agents/skills/feature-engineering-cookbook/SKILL.md`, `.agents/skills/model-selection-guide/SKILL.md`

## 실행 원칙

- 전체 작업은 `ml-experiment` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- ML 실험 관리의 데이터준비→모델설계→학습→평가→배포를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_data_preparation.md` — 데이터 준비 계획 및 파이프라인
- `02_model_design.md` — 모델 아키텍처 설계
- `03_training_config.md` — 학습 설정 및 실험 추적
- `04_evaluation_report.md` — 평가 보고서
- `05_review_report.md` — 실험 리뷰 보고서
- `experiment_code/` — 실험 구현 코드
