---
name: open-source-launcher
description: >-
  Trigger when: 사용자가 `open-source-launcher` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Open Source Launcher Harness

오픈소스 프로젝트 런칭의 코드정리→문서→라이선스→커뮤니티 구축을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `code-organizer`: 코드 정리자. 오픈소스 공개를 위한 코드 구조 재편, 민감정보 제거, 코딩 표준 적용, 의존성 정리, 빌드 시스템 구성을 수행한다.
- `community-manager`: 커뮤니티 매니저. 프로젝트 거버넌스, Code of Conduct, 이슈/PR 템플릿, CI/CD 파이프라인, 릴리스 전략, 커뮤니티 채널을 설계·구성한다.
- `doc-writer`: 문서 작성자. README, CONTRIBUTING, API 문서, 튜토리얼, CHANGELOG 등 오픈소스 프로젝트에 필수적인 문서 패키지를 작성한다.
- `launch-reviewer`: 런칭 리뷰어(QA). 코드정리-문서-라이선스-커뮤니티 간의 정합성을 교차 검증하고, 오픈소스 런칭 준비도를 평가하며, 최종 체크리스트를 제공한다.
- `license-specialist`: 라이선스 전문가. 오픈소스 라이선스 선정, 의존성 라이선스 호환성 검증, 저작권 고지, CLA/DCO 설정을 수행한다.

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
- `01_code_organization.md` — 코드 정리 계획 및 결과
- `02_documentation.md` — 문서 패키지 (README, 가이드 등)
- `03_license_review.md` — 라이선스 검토 및 선정
- `04_community_setup.md` — 커뮤니티 구성 및 거버넌스
- `05_launch_report.md` — 런칭 리뷰 보고서
- `generated_files/` — 생성된 파일들 (README, LICENSE, CONTRIBUTING 등)

## 확장 스킬

- `.agents/skills/community-health-metrics/SKILL.md`
- `.agents/skills/license-compatibility-matrix/SKILL.md`
