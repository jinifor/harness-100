---
name: infra-as-code
description: >-
  Trigger when: 사용자가 `infra-as-code` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Infra as Code Harness

Infrastructure as Code(IaC) 설계 및 구현을 에이전트 팀이 협업하여 수행하는 하네스. Terraform/Pulumi 기반 환경 구성, 보안, 비용 최적화 파이프라인을 자동화한다.

## Specialist Agents

- `cost-optimizer`: 클라우드 비용 최적화 전문가. 리소스 사이징, 예약 인스턴스, 스팟 활용, FinOps 문화를 기반으로 인프라 비용을 최적화한다.
- `drift-detector`: 드리프트 감지 전문가. IaC 상태와 실제 인프라 간의 차이를 감지하고, 정책 준수를 검증하며, 자동 교정 전략을 수립한다.
- `iac-reviewer`: IaC 리뷰어(QA). 설계-보안-비용-드리프트 간의 정합성을 교차 검증하고, IaC 베스트 프랙티스 준수를 확인한다.
- `infra-architect`: 인프라 설계 전문가. 클라우드 아키텍처를 설계하고, Terraform/Pulumi 모듈 구조를 정의하며, 환경별 분리 전략과 상태 관리를 수립한다.
- `security-engineer`: 인프라 보안 전문가. IAM 정책, 네트워크 보안, 데이터 암호화, 컴플라이언스 준수를 설계하고 보안 정책을 코드로 구현한다.

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
- `01_infra_design.md` — 인프라 설계서
- `02_security_design.md` — 보안 설계서
- `03_cost_analysis.md` — 비용 분석 보고서
- `04_drift_policy.md` — 드리프트 감지 정책
- `05_review_report.md` — 최종 리뷰 보고서

## 확장 스킬

- `.agents/skills/cloud-cost-models/SKILL.md`
- `.agents/skills/terraform-module-patterns/SKILL.md`
