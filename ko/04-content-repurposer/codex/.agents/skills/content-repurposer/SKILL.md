---
name: content-repurposer
description: >-
  1개 원본 콘텐츠를 블로그, SNS, 프레젠테이션 등 다양한 포맷으로 다중 변환하는 오케스트레이션 skill.
  Trigger when: 사용자가 콘텐츠 리퍼포징, 블로그 변환, SNS 변환, 프레젠테이션 변환, 또는 전체 재활용 흐름을 요청할 때.
  Do not trigger when: 단일 포맷의 짧은 수정, 다른 플랫폼 제작, 또는 실제 이미지/발행 자동화를 요청할 때.
  Expected input: 원본 콘텐츠, 목표 포맷, 타깃 독자, 톤, 제약 조건.
  Expected output: `_workspace/` 산출물과 리뷰 보고서.
---

# Content Repurposer

원본 콘텐츠를 블로그→SNS→프레젠테이션으로 에이전트 팀이 협업하여 한 번에 변환한다.

## 역할

- `source-analyst`: 원본 분석, 변환 전략
- `blog-writer`: 블로그 포스트
- `sns-copywriter`: 플랫폼별 SNS 포스트
- `presentation-builder`: 슬라이드 프레젠테이션
- `quality-reviewer`: 전 항목 교차 검증

## 실행 순서

1. 입력을 정리해 `_workspace/00_input.md`로 저장한다.
2. `source-analyst`가 `_workspace/01_source_analysis.md`를 만든다.
3. `blog-writer`, `sns-copywriter`, `presentation-builder`를 병렬로 실행한다.
4. `quality-reviewer`가 전체 산출물을 검토한다.

## 작업 규칙

- 모든 산출물은 `_workspace/`에 저장 가능해야 한다.
- 리뷰는 읽기 전용으로 하고 findings를 먼저 제시한다.
- 원본의 핵심 메시지를 왜곡하지 않는다.
- 문서에 없는 script, asset, config key는 만들지 않는다.

## 산출물

- `_workspace/01_source_analysis.md`
- `_workspace/02_blog_post.md`
- `_workspace/03_sns_package.md`
- `_workspace/04_presentation.md`
- `_workspace/05_review_report.md`

## 확장 스킬

- `.agents/skills/platform-adaptation/SKILL.md`
- `.agents/skills/content-atomization/SKILL.md`
