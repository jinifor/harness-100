---
name: podcast-studio
description: >-
  팟캐스트 에피소드의 기획, 리서치, 대본, 쇼노트, 배포를 Codex 에이전트 팀이 함께 생성하는 오케스트레이션 skill.
  Trigger when: 사용자가 팟캐스트 기획, 에피소드 대본, 쇼노트, 배포 패키지, 또는 전체 프로덕션을 요청할 때.
  Do not trigger when: 단일 질문 수준의 일반 정보 요청, 다른 플랫폼 콘텐츠 제작, 또는 실제 오디오 편집/RSS 설정을 요청할 때.
  Expected input: 주제, 게스트 정보, 톤, 길이, 기존 파일.
  Expected output: `_workspace/` 산출물과 리뷰 보고서.
---

# Podcast Studio

팟캐스트 에피소드의 기획, 리서치, 대본, 쇼노트, 배포를 에이전트 팀이 협업하여 한 번에 생성한다.

## 역할

- `researcher`: 주제 조사, 팩트체크
- `scriptwriter`: 대본 작성, 질문 흐름
- `shownote-editor`: 쇼노트, 타임스탬프, 참고자료
- `distribution-manager`: 플랫폼 메타데이터, 홍보 카피
- `production-reviewer`: 전 항목 교차 검증

## 실행 순서

1. 입력을 정리해 `_workspace/00_input.md`로 저장한다.
2. `researcher`가 `_workspace/01_research_brief.md`를 만든다.
3. `scriptwriter`가 `_workspace/02_script.md`를 만든다.
4. `shownote-editor`와 `distribution-manager`를 병렬로 실행한다.
5. `production-reviewer`가 전체 산출물을 검토한다.

## 작업 규칙

- 모든 산출물은 `_workspace/`에 저장 가능해야 한다.
- 기존 파일이 있으면 적절한 위치로 복사하고 해당 단계를 건너뛴다.
- 리뷰는 읽기 전용으로 하고 findings를 먼저 제시한다.
- 문서에 없는 script, asset, config key는 만들지 않는다.

## 산출물

- `_workspace/01_research_brief.md`
- `_workspace/02_script.md`
- `_workspace/03_shownotes.md`
- `_workspace/04_distribution_package.md`
- `_workspace/05_review_report.md`

## 확장 스킬

- `.agents/skills/interview-techniques/SKILL.md`
- `.agents/skills/audio-storytelling/SKILL.md`
- `.agents/skills/podcast-growth/SKILL.md`
