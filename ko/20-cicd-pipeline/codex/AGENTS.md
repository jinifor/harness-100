# CI/CD Pipeline Harness Codex 지침

## 목적

- 이 디렉토리는 `CI/CD Pipeline Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/cicd-pipeline/SKILL.md`
- 전문 agent: `.codex/agents/infra-engineer.toml`, `.codex/agents/monitoring-specialist.toml`, `.codex/agents/pipeline-designer.toml`, `.codex/agents/pipeline-reviewer.toml`, `.codex/agents/security-scanner.toml`
- 확장 스킬: `.agents/skills/deployment-strategies/SKILL.md`, `.agents/skills/pipeline-security-gates/SKILL.md`

## 실행 원칙

- 전체 작업은 `cicd-pipeline` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- CI/CD 파이프라인의 설계·구축·모니터링·최적화를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_pipeline_design.md` — 파이프라인 설계 문서
- `02_pipeline_config/` — 파이프라인 설정 파일 (YAML 등)
- `03_monitoring.md` — 모니터링 설계 문서
- `04_security_scan.md` — 보안 스캔 설정 및 보고서
- `05_review_report.md` — 파이프라인 리뷰 보고서
