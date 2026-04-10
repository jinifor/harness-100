---
name: youtube-production
description: >-
  YouTube 영상 콘텐츠의 기획, 대본, 썸네일, SEO를 Codex 에이전트 팀이 협업하여 한 번에 생성하는 오케스트레이션 skill.
  Trigger when: 사용자가 유튜브 영상 기획, 영상 대본, 썸네일 컨셉, SEO 패키지, 또는 전체 프로덕션을 요청할 때.
  Do not trigger when: 단일 사실 질문, 다른 플랫폼 콘텐츠 제작, 또는 실제 영상 편집/Analytics API 연동을 요청할 때.
  Expected input: 주제, 채널 정보, 제약 조건, 기존 파일.
  Expected output: `_workspace/` 산출물과 리뷰 보고서.
---

# YouTube Production

YouTube 영상의 기획, 대본, 썸네일, SEO를 에이전트 팀이 협업하여 한 번에 생성한다.

## 역할

- `content-strategist`: 영상 컨셉, 경쟁 분석, 키워드 맵
- `scriptwriter`: 타임코드 기반 대본, 훅, 전환, CTA
- `thumbnail-designer`: 썸네일 컨셉, 텍스트 오버레이, 이미지 프롬프트
- `seo-optimizer`: 제목, 설명, 태그, 챕터, 자막
- `production-reviewer`: 전 항목 교차 검증

## 실행 순서

1. 입력을 정리해 `_workspace/00_input.md`로 저장한다.
2. `content-strategist`가 `_workspace/01_strategist_brief.md`를 만든다.
3. `scriptwriter`와 `thumbnail-designer`를 병렬로 실행한다.
4. `seo-optimizer`가 대본과 전략을 바탕으로 SEO 패키지를 만든다.
5. `production-reviewer`가 전체 산출물을 검토한다.
6. 리뷰 지적을 반영해 필요한 경우 재작업한다.

## 작업 규칙

- 모든 산출물은 `_workspace/`에 저장 가능해야 한다.
- 검색 데이터가 필요한 부분은 웹 검색을 사용한다.
- 이미지 생성이 실패해도 썸네일 프롬프트는 남긴다.
- 리뷰는 읽기 전용으로 하고 findings를 먼저 제시한다.
- 문서에 없는 script, asset, config key는 만들지 않는다.

## 산출물

- `_workspace/01_strategist_brief.md`
- `_workspace/02_scriptwriter_script.md`
- `_workspace/03_thumbnail_concept.md`
- `_workspace/04_seo_package.md`
- `_workspace/05_review_report.md`
- `_workspace/subtitle.srt`

## 확장 스킬

- `.agents/skills/hook-writing/SKILL.md`
- `.agents/skills/thumbnail-psychology/SKILL.md`
