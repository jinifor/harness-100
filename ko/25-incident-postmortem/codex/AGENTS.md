# Incident Postmortem Harness Codex 지침

## 목적

- 이 디렉토리는 `Incident Postmortem Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/incident-postmortem/SKILL.md`
- 전문 agent: `.codex/agents/impact-assessor.toml`, `.codex/agents/postmortem-reviewer.toml`, `.codex/agents/remediation-planner.toml`, `.codex/agents/root-cause-investigator.toml`, `.codex/agents/timeline-reconstructor.toml`
- 확장 스킬: `.agents/skills/rca-methodology/SKILL.md`, `.agents/skills/sla-impact-calculator/SKILL.md`

## 실행 원칙

- 전체 작업은 `incident-postmortem` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 장애 사후분석 보고서를 에이전트 팀이 협업하여 생성하는 하네스. 타임라인 재구성→근본원인 분석→영향범위 산정→재발방지 대책→보고서 생성 파이프라인을 자동화한다.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_timeline.md` — 장애 타임라인
- `02_root_cause.md` — 근본원인 분석
- `03_impact_assessment.md` — 영향범위 산정
- `04_remediation_plan.md` — 재발방지 대책
- `05_review_report.md` — 리뷰 보고서
- `postmortem_report.md` — 최종 통합 포스트모텀 보고서
