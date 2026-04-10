---
name: course-builder
description: >-
  Trigger when: 사용자가 `course-builder` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Course Builder Harness

온라인 강의 설계의 커리큘럼→교안→퀴즈→실습과제를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `content-writer`: 강의 콘텐츠 작성자. 커리큘럼을 기반으로 레슨별 교안, 강의 슬라이드 구성, 강사 노트, 학습자 핸드아웃을 작성한다.
- `course-reviewer`: 과정검증자(QA). 커리큘럼-교안-퀴즈-실습 간의 학습목표 정렬을 교차 검증하고, 난이도 일관성, 커버리지, 품질 문제를 발견하여 피드백을 제공한다.
- `curriculum-designer`: 교육설계자. 학습목표 수립, 커리큘럼 구조 설계, 모듈/레슨 분할, 선수학습 매핑, 학습경로 설계를 수행한다. ADDIE 모델과 블룸의 분류학에 기반한 체계적 교수설계를 수행한다.
- `lab-designer`: 실습설계자. 학습목표에 정렬된 실습과제, 미니 프로젝트, 캡스톤 프로젝트를 설계한다. 평가 루브릭, 예시 솔루션, 스캐폴딩을 포함한다.
- `quiz-maker`: 퀴즈 출제자. 학습목표에 정렬된 형성평가(레슨별 퀴즈)와 총괄평가(모듈/과정 시험)를 설계한다. 블룸의 분류학에 따른 다양한 문항 유형과 피드백을 포함한다.

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
- `01_curriculum.md` — 커리큘럼/과정 설계서
- `02_lesson_plans.md` — 교안/강의노트
- `03_quizzes.md` — 퀴즈/평가 문항
- `04_labs.md` — 실습과제/프로젝트
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/assessment-engineering/SKILL.md`
- `.agents/skills/lab-scaffolding/SKILL.md`
- `.agents/skills/learning-design/SKILL.md`
