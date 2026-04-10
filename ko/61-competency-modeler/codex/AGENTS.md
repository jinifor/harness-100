# Competency Modeler Harness Codex 지침

## 목적

- 이 디렉토리는 `Competency Modeler Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/competency-modeler/SKILL.md`
- 전문 agent: `.codex/agents/competency-architect.toml`, `.codex/agents/development-planner.toml`, `.codex/agents/job-analyst.toml`, `.codex/agents/rubric-designer.toml`
- 확장 스킬: `.agents/skills/bars-assessment/SKILL.md`, `.agents/skills/ksa-taxonomy/SKILL.md`

## 실행 원칙

- 전체 작업은 `competency-modeler` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 역량 모델링의 직무분석→역량사전작성→평가루브릭설계→개발계획수립→역량매트릭스를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_job_analysis.md` — 직무 분석서
- `02_competency_dictionary.md` — 역량 사전
- `03_assessment_rubric.md` — 평가 루브릭
- `04_development_plan.md` — 역량 개발 계획서
- `05_competency_matrix.md` — 역량 매트릭스
