---
name: fullstack-webapp
description: >-
  Trigger when: 사용자가 `fullstack-webapp` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Fullstack Web App Harness

풀스택 웹앱의 요구사항→설계→프론트엔드→백엔드→테스트→배포를 에이전트 팀이 협업하여 개발하는 하네스.

## Specialist Agents

- `architect`: 시스템 아키텍트. 요구사항을 분석하고 시스템 아키텍처, 기술 스택, DB 모델링, API 설계를 수행한다. 프론트엔드/백엔드/QA/DevOps 팀이 즉시 작업할 수 있는 설계 문서를 산출한다.
- `backend-dev`: 백엔드 개발자. API 구현, 데이터베이스 연동, 인증/인가, 비즈니스 로직을 개발한다. 아키텍처 설계의 API 명세와 DB 스키마를 코드로 구현한다.
- `devops-engineer`: DevOps 엔지니어. CI/CD 파이프라인 구축, 인프라 설정, 배포 자동화, 모니터링 설정을 담당한다. 개발부터 프로덕션까지의 배포 경로를 설계하고 구현한다.
- `frontend-dev`: 프론트엔드 개발자. 아키텍처 설계를 기반으로 React/Next.js 프론트엔드를 구현한다. UI 컴포넌트, 페이지 라우팅, 상태관리, API 연동, 반응형 디자인을 담당한다.
- `qa-engineer`: QA 엔지니어. 테스트 전략을 수립하고, 단위/통합/E2E 테스트를 작성하며, 코드 품질과 기능 정합성을 검증한다.

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

- `_workspace/00_input.md` — 사용자 입력 정리
- `_workspace/01_architecture.md` — 아키텍처 설계 문서
- `_workspace/02_api_spec.md` — API 명세
- `_workspace/03_db_schema.md` — DB 스키마
- `_workspace/04_test_plan.md` — 테스트 계획
- `_workspace/05_deploy_guide.md` — 배포 가이드
- `_workspace/06_review_report.md` — 리뷰 보고서
- `src/` — 소스 코드 (프론트엔드 + 백엔드)

## 확장 스킬

- `.agents/skills/api-security-checklist/SKILL.md`
- `.agents/skills/component-patterns/SKILL.md`
