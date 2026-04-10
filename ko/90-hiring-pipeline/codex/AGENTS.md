# Hiring Pipeline Harness Codex 지침

## 목적

- 이 디렉토리는 `Hiring Pipeline Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/hiring-pipeline/SKILL.md`
- 전문 agent: `.codex/agents/interview-designer.toml`, `.codex/agents/jd-writer.toml`, `.codex/agents/offer-coordinator.toml`, `.codex/agents/screening-expert.toml`, `.codex/agents/sourcing-specialist.toml`
- 확장 스킬: `.agents/skills/competency-model/SKILL.md`, `.agents/skills/interview-scorecard/SKILL.md`

## 실행 원칙

- 전체 작업은 `hiring-pipeline` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 채용 프로세스: JD작성→소싱→스크리닝→면접→평가→오퍼까지 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_job_description.md` — 직무기술서 및 채용공고
- `02_sourcing_strategy.md` — 소싱 전략
- `03_screening_framework.md` — 스크리닝 프레임워크
- `04_interview_design.md` — 면접 설계서
- `05_evaluation_offer.md` — 최종 평가 및 오퍼 가이드
