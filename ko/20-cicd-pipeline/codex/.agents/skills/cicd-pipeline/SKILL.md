---
name: cicd-pipeline
description: >-
  Trigger when: 사용자가 `cicd-pipeline` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# CI/CD Pipeline Harness

CI/CD 파이프라인의 설계·구축·모니터링·최적화를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `infra-engineer`: 인프라 엔지니어. CI/CD 러너 구성, 컨테이너 빌드(Dockerfile, docker-compose), 환경변수/시크릿 관리, 아티팩트 저장소, 인프라 프로비저닝(Terraform)을 설계하고 구현한다.
- `monitoring-specialist`: CI/CD 모니터링 전문가. 파이프라인 메트릭(빌드 시간, 성공률, 배포 빈도), 알림 설정(Slack, PagerDuty), 대시보드, DORA 메트릭, SLA/SLO 설계를 수행한다.
- `pipeline-designer`: CI/CD 파이프라인 설계자. 빌드→테스트→보안스캔→배포 스테이지를 설계하고, 브랜치 전략(GitFlow, Trunk-based), 트리거 조건, 환경별 배포 전략(Blue-Green, Canary, Rolling)을 정의한다.
- `pipeline-reviewer`: CI/CD 파이프라인 리뷰어(QA). 파이프라인 효율성, 안정성, 보안, 설계-구현 정합성을 교차 검증한다.
- `security-scanner`: CI/CD 보안 스캐너. SAST(정적 분석), DAST(동적 분석), SCA(의존성 취약점), 컨테이너 이미지 스캔, 시크릿 탐지를 파이프라인에 통합한다.

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
- `01_pipeline_design.md` — 파이프라인 설계 문서
- `02_pipeline_config/` — 파이프라인 설정 파일 (YAML 등)
- `03_monitoring.md` — 모니터링 설계 문서
- `04_security_scan.md` — 보안 스캔 설정 및 보고서
- `05_review_report.md` — 파이프라인 리뷰 보고서

## 확장 스킬

- `.agents/skills/deployment-strategies/SKILL.md`
- `.agents/skills/pipeline-security-gates/SKILL.md`
