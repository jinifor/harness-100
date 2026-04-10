---
name: patent-drafter
description: >-
  Trigger when: 사용자가 `patent-drafter` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Patent Drafter Harness

특허 명세서 작성 — 선행기술조사→청구항→명세서→도면설명을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `claim-drafter`: 청구항 작성자. 선행기술 조사 결과를 기반으로 최적의 권리범위를 설계하고, 독립항·종속항을 체계적으로 작성한다.
- `drawing-designer`: 도면 설계자. 특허 명세서의 도면 구성을 설계하고, 각 도면의 상세 설명과 부호 배치를 정의한다. 텍스트 기반 도면 명세를 작성한다.
- `patent-reviewer`: 특허 검증자. 청구항-명세서-도면 간 정합성을 교차 검증하고, 기재불비·신규성·진보성 관점에서 거절 이유를 사전 점검한다.
- `prior-art-researcher`: 선행기술 조사원. 발명과 관련된 기존 특허, 논문, 기술 문헌을 조사하고, 신규성·진보성 관점에서 차별점을 분석한다.
- `specification-writer`: 명세서 작성자. 청구항을 완전히 지지(support)하는 발명의 상세한 설명을 작성한다. 기술 분야, 배경기술, 해결 과제, 과제 해결 수단, 발명의 효과, 실시예를 포함한다.

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

- `00_input.md` — 사용자 입력 정리 (발명 개요)
- `01_prior_art_report.md` — 선행기술 조사 보고서
- `02_claims.md` — 청구항 세트
- `03_specification.md` — 발명의 상세한 설명
- `04_drawings.md` — 도면 설명서
- `05_review_report.md` — 검증 보고서

## 확장 스킬

- `.agents/skills/claim-drafting-patterns/SKILL.md`
- `.agents/skills/prior-art-search-strategy/SKILL.md`
