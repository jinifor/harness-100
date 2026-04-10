---
name: newsletter-engine
description: >-
  뉴스레터 콘텐츠를 큐레이션, 작성, A/B 테스트, 최종 편집까지 Codex 에이전트 팀이 함께 생성하는 오케스트레이션 skill.
  Trigger when: 사용자가 뉴스레터 기획, 초안, A/B 테스트, 최종 편집, 또는 전체 발행 흐름을 요청할 때.
  Do not trigger when: 단일 문단 수정, 다른 플랫폼 콘텐츠 제작, 또는 메일 발송 자동화를 요청할 때.
  Expected input: 주제, 브랜드 톤, 독자, 기존 파일.
  Expected output: `_workspace/` 산출물과 리뷰 보고서.
---

# Newsletter Engine

뉴스레터 콘텐츠를 큐레이션→작성→A/B 테스트→최종 편집 순서로 생성한다.

## 역할

- `curator`: 소스 수집, 트렌드 분석
- `copywriter`: 제목, 본문, CTA
- `analyst`: A/B 테스트, 발송 최적화
- `editor-in-chief`: 톤 일관성, 최종 편집
- `quality-reviewer`: 전 항목 교차 검증

## 실행 순서

1. 입력을 정리해 `_workspace/00_input.md`로 저장한다.
2. `curator`가 `_workspace/01_curation_brief.md`를 만든다.
3. `copywriter`가 `_workspace/02_newsletter_draft.md`를 만든다.
4. `analyst`가 `_workspace/03_ab_test_plan.md`를 만든다.
5. `editor-in-chief`가 `_workspace/04_editorial_final.md`를 만든다.
6. `quality-reviewer`가 전체 산출물을 검토한다.

## 작업 규칙

- 모든 산출물은 `_workspace/`에 저장 가능해야 한다.
- 리뷰는 읽기 전용으로 하고 findings를 먼저 제시한다.
- 법적 요소와 모바일 가독성을 함께 확인한다.
- 문서에 없는 script, asset, config key는 만들지 않는다.

## 산출물

- `_workspace/01_curation_brief.md`
- `_workspace/02_newsletter_draft.md`
- `_workspace/03_ab_test_plan.md`
- `_workspace/04_editorial_final.md`
- `_workspace/05_review_report.md`

## 확장 스킬

- `.agents/skills/email-copywriting/SKILL.md`
- `.agents/skills/audience-segmentation/SKILL.md`
- `.agents/skills/deliverability-optimization/SKILL.md`
