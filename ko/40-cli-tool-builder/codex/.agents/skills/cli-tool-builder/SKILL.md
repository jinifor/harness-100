---
name: cli-tool-builder
description: >-
  Trigger when: 사용자가 `cli-tool-builder` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# CLI Tool Builder Harness

CLI 도구 개발의 명령설계→파서→핸들러→테스트→문서→배포설정을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `command-designer`: CLI 명령 설계자. 서브커맨드 체계, 옵션/인자 구조, UX 가이드라인을 설계한다. POSIX 컨벤션과 현대 CLI 모범 사례를 적용한다.
- `core-developer`: CLI 코어 개발자. 명령 파서, 핸들러 함수, 비즈니스 로직을 구현한다. 클린 아키텍처와 테스트 용이성을 보장한다.
- `docs-writer`: CLI 문서 작성자. man page, --help 텍스트, README, 튜토리얼, 사용 예제를 작성한다. 사용자가 도구를 즉시 활용할 수 있는 문서를 제공한다.
- `release-engineer`: 릴리스 엔지니어. CLI 도구의 빌드, 패키징, 배포 파이프라인을 구성한다. PyPI/npm/Homebrew/GitHub Releases 배포를 설정한다.
- `test-engineer`: CLI 테스트 엔지니어. 단위 테스트, 통합 테스트, E2E 테스트를 작성한다. 명령어 조합, 에러 케이스, 파이프라인 호환성을 검증한다.

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
- `01_command_design.md` — 명령 체계 설계서
- `02_core_implementation.md` — 코어 구현 문서
- `03_test_suite.md` — 테스트 스위트
- `04_documentation.md` — 사용자 문서
- `05_release_config.md` — 릴리스 설정
- `src/` — CLI 소스코드

## 확장 스킬

- `.agents/skills/arg-parser-generator/SKILL.md`
- `.agents/skills/ux-linter/SKILL.md`
