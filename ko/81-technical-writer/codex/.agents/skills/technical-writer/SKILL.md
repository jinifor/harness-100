---
name: technical-writer
description: >-
  Trigger when: 사용자가 `technical-writer` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Technical Writer Harness

기술 문서 작성의 구조설계→집필→다이어그램→리뷰→버전관리를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `diagram-maker`: 다이어그램 작성자. Mermaid 문법으로 아키텍처 다이어그램, 시퀀스 다이어그램, 플로차트 등 기술 문서용 시각 자료를 생성한다.
- `doc-writer`: 기술 문서 집필자. 정보 설계에 따라 본문을 작성하고, 코드 예제와 튜토리얼을 포함한 완성도 높은 기술 문서를 생성한다.
- `info-architect`: 정보 설계자. 기술 문서의 독자를 분석하고, 최적의 문서 구조와 목차를 설계하며, 문서 유형별 템플릿을 제공한다.
- `tech-reviewer`: 기술 리뷰어(QA). 문서의 기술적 정확성, 완전성, 일관성, 독자 적합성을 검증하고 구체적 수정 피드백을 제공한다.
- `version-controller`: 버전 관리자. 문서의 메타데이터, 변경 이력, 버전 번호를 관리하고, 배포 준비 상태를 확인한다.

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
- `01_doc_structure.md` — 문서 구조 설계서
- `02_doc_draft.md` — 문서 본문 초안
- `03_diagrams.md` — 다이어그램 모음
- `04_review_report.md` — 기술 리뷰 보고서
- `05_version_meta.md` — 버전 관리 메타데이터

## 확장 스킬

- `.agents/skills/api-doc-standards/SKILL.md`
- `.agents/skills/code-example-patterns/SKILL.md`
- `.agents/skills/diagram-patterns/SKILL.md`
