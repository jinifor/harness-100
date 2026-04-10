# Risk Register Harness Codex 지침

## 목적

- 이 디렉토리는 `Risk Register Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/risk-register/SKILL.md`
- 전문 agent: `.codex/agents/assessment-analyst.toml`, `.codex/agents/monitoring-planner.toml`, `.codex/agents/report-writer.toml`, `.codex/agents/response-strategist.toml`, `.codex/agents/risk-identifier.toml`
- 확장 스킬: `.agents/skills/risk-response-patterns/SKILL.md`, `.agents/skills/risk-scoring-matrix/SKILL.md`

## 실행 원칙

- 전체 작업은 `risk-register` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 프로젝트 리스크 관리대장: 리스크식별→확률·영향평가→대응전략수립→모니터링계획→상태보고서까지 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_risk_identification.md` — 리스크 식별 보고서
- `02_risk_assessment.md` — 확률·영향 평가 매트릭스
- `03_response_strategy.md` — 대응 전략 계획서
- `04_monitoring_plan.md` — 모니터링 계획
- `05_status_report.md` — 리스크 상태 보고서
