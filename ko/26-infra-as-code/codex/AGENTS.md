# Infra as Code Harness Codex 지침

## 목적

- 이 디렉토리는 `Infra as Code Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/infra-as-code/SKILL.md`
- 전문 agent: `.codex/agents/cost-optimizer.toml`, `.codex/agents/drift-detector.toml`, `.codex/agents/iac-reviewer.toml`, `.codex/agents/infra-architect.toml`, `.codex/agents/security-engineer.toml`
- 확장 스킬: `.agents/skills/cloud-cost-models/SKILL.md`, `.agents/skills/terraform-module-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `infra-as-code` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- Infrastructure as Code(IaC) 설계 및 구현을 에이전트 팀이 협업하여 수행하는 하네스. Terraform/Pulumi 기반 환경 구성, 보안, 비용 최적화 파이프라인을 자동화한다.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_infra_design.md` — 인프라 설계서
- `02_security_design.md` — 보안 설계서
- `03_cost_analysis.md` — 비용 분석 보고서
- `04_drift_policy.md` — 드리프트 감지 정책
- `05_review_report.md` — 최종 리뷰 보고서
