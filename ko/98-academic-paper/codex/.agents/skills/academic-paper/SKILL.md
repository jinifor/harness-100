---
name: academic-paper
description: >-
  Trigger when: 사용자가 `academic-paper` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Academic Paper Harness

학술 논문 작성의 연구설계→실험→분석→집필→투고준비를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `experiment-manager`: 학술 실험 관리자. 연구 설계를 기반으로 실험 프로토콜, 데이터 수집 절차, 도구/설문 설계, 파일럿 테스트 계획을 수립한다.
- `paper-writer`: 학술 논문 작성자. IMRaD 구조에 따라 학술 논문을 집필하며, 학술적 글쓰기 규범과 인용 관리를 수행한다.
- `research-designer`: 학술 연구 설계자. 연구 질문 정립, 가설 수립, 연구 방법론 선택, 변수 정의, 선행연구 분석을 수행한다.
- `statistical-analyst`: 학술 통계 분석가. 연구 설계에 맞는 통계 분석 전략을 수립하고, 분석 코드를 생성하며, 결과를 해석하고 시각화한다.
- `submission-preparer`: 학술 논문 투고 준비자. 타깃 저널 선정, 저널별 포맷팅, 커버레터, 리뷰어 추천, 체크리스트를 관리한다.

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
- `01_research_design.md` — 연구 설계서
- `02_experiment_protocol.md` — 실험 프로토콜
- `03_analysis_report.md` — 분석 보고서
- `04_manuscript.md` — 논문 원고
- `05_submission_package.md` — 투고 패키지
- `06_review_report.md` — 통합 리뷰 보고서

## 확장 스킬

- `.agents/skills/citation-standards/SKILL.md`
- `.agents/skills/research-methodology/SKILL.md`
