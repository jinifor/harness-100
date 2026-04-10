---
name: changelog-generator
description: >-
  Trigger when: 사용자가 `changelog-generator` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Changelog Generator Harness

릴리스 관리의 git이력분석→변경분류→릴리스노트생성→마이그레이션가이드→공지문작성을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `announcement-writer`: 공지문 작성자. 릴리스 정보를 블로그 포스트, SNS 게시물, 이메일 뉴스레터 등 다양한 채널에 맞는 형태로 작성한다.
- `change-classifier`: 변경 분류자. 커밋 분석 결과를 기반으로 모든 변경사항을 의미 단위로 그룹핑하고, 사용자 영향도에 따라 분류한다.
- `commit-analyst`: 커밋 분석가. git 이력을 분석하여 두 버전 사이의 모든 변경사항을 추출한다. 커밋 메시지, PR, 브랜치 전략, 기여자 정보를 파악한다.
- `migration-guide-writer`: 마이그레이션 가이드 작성자. Breaking Change에 대한 상세 업그레이드 가이드를 작성한다. 코드 변환 예시, 단계별 절차, 호환성 매트릭스를 제공한다.
- `release-note-writer`: 릴리스 노트 작성자. 변경 분류 결과를 기반으로 사용자 친화적인 릴리스 노트를 작성한다. CHANGELOG.md, GitHub Release 형식을 지원한다.

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
- `01_commit_analysis.md` — 커밋 분석 보고서
- `02_change_classification.md` — 변경 분류 결과
- `03_release_notes.md` — 릴리스 노트
- `04_migration_guide.md` — 마이그레이션 가이드
- `05_announcement.md` — 공지문 (블로그/SNS/이메일)

## 확장 스킬

- `.agents/skills/commit-parser/SKILL.md`
- `.agents/skills/semver-analyzer/SKILL.md`
