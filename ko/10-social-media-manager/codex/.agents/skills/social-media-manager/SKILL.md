---
name: social-media-manager
description: >-
  Trigger when: 사용자가 `social-media-manager` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Social Media Manager Harness

SNS 콘텐츠 달력·포스트작성·해시태그·성과분석을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `copywriter`: SNS 카피라이터. 플랫폼별 특성에 맞는 포스트 카피, 캡션, CTA를 작성한다. 인스타그램 캡션, 트위터 스레드, 틱톡 스크립트, 링크드인 포스트 등 각 플랫폼의 문법에 최적화한다.
- `hashtag-analyst`: 해시태그 분석가. 포스트별 최적 해시태그 세트를 설계하고, 트렌드 해시태그 분석, 경쟁 해시태그 조사, 브랜드 해시태그 전략을 수립한다.
- `performance-reviewer`: SNS 성과검증자(QA). 전략-포스트-비주얼-해시태그 간의 일관성을 교차 검증하고, KPI 정렬, 플랫폼 적합성, 브랜드 일관성을 확인하여 피드백을 제공한다.
- `sns-strategist`: SNS 전략가. 채널별 특성 분석, 타깃 오디언스 정의, 콘텐츠 달력 설계, 캠페인 구조 기획을 수행한다. 플랫폼별(인스타그램, 트위터/X, 틱톡, 페이스북, 링크드인) 최적화된 전략을 수립한다.
- `visual-planner`: SNS 비주얼 기획자. 포스트별 이미지 컨셉, 카드뉴스 구성, 릴스/숏폼 스토리보드, 비주얼 가이드라인을 설계한다.

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
- `01_strategy.md` — SNS 전략/콘텐츠 달력
- `02_posts.md` — 포스트 카피 모음
- `03_visuals.md` — 비주얼 기획서
- `04_hashtags.md` — 해시태그 전략서
- `05_review_report.md` — 리뷰 보고서

## 확장 스킬

- `.agents/skills/hashtag-science/SKILL.md`
- `.agents/skills/platform-algorithms/SKILL.md`
- `.agents/skills/viral-copywriting/SKILL.md`
