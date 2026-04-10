---
name: book-publishing
description: >-
  Trigger when: 사용자가 `book-publishing` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Book Publishing Harness

전자책 출판의 원고편집→표지→목차→메타데이터→배포를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `cover-designer`: 표지 디자이너. 책의 장르·톤·타깃에 맞는 표지 컨셉을 설계하고, Gemini 이미지 생성으로 표지를 제작한다. 타이포그래피, 컬러, 구도를 포함한다.
- `manuscript-editor`: 원고 편집자. 구조 편집(챕터 구성, 흐름), 문체 교정(톤 통일, 가독성), 내용 일관성 검증을 수행한다. 발전적 편집과 라인 편집을 모두 포함한다.
- `metadata-manager`: 메타데이터 관리자. ISBN, 도서 분류(BISAC/KDC), 도서 설명문, 키워드, 가격 설정, 배포 플랫폼 설정을 수행한다. 전자책 유통에 필요한 모든 메타데이터를 관리한다.
- `proofreader`: 교정교열자. 맞춤법, 문법, 띄어쓰기, 외래어 표기, 숫자 표기, 문장부호, 용어 통일을 검수한다. 한국어 어문 규정에 기반한 정밀 교정을 수행한다.
- `publishing-reviewer`: 출판 검증자(QA). 원고-교정-표지-메타데이터 간의 일관성을 교차 검증하고, 출판 규격 준수, 법적 요건, 배포 준비 상태를 최종 확인한다.

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
- `01_edited_manuscript.md` — 편집된 원고
- `02_proofread_report.md` — 교정교열 보고서
- `03_cover_concept.md` — 표지 컨셉/이미지
- `04_metadata.md` — 메타데이터/배포 설정
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/book-metadata-seo/SKILL.md`
- `.agents/skills/cover-design-psychology/SKILL.md`
- `.agents/skills/developmental-editing/SKILL.md`
