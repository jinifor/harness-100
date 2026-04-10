---
name: personal-branding
description: >-
  Trigger when: 사용자가 `personal-branding` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Personal Branding Harness

개인 브랜딩 에이전트 팀 하네스.

## Specialist Agents

- `cover-letter-writer`: 자기소개서·커버레터 작성 전문가. 타깃 포지션에 맞춤화된, 진정성 있으면서도 전략적인 자기소개서와 커버레터를 작성한다.
- `portfolio-designer`: 포트폴리오 설계자. 핵심 프로젝트를 큐레이션하고, 각 프로젝트의 스토리텔링 구조를 설계하며, 포트폴리오 사이트/문서의 전체 구성을 기획한다.
- `positioning-strategist`: 포지셔닝 전략가. 개인의 강점·경험·목표를 분석하고, 타깃 시장에서의 차별화 포인트와 브랜드 내러티브를 설계한다.
- `profile-optimizer`: LinkedIn 프로필 최적화 전문가. 검색 노출을 극대화하고, 채용 담당자의 관심을 끄는 프로필 콘텐츠를 작성한다.
- `resume-writer`: 이력서·CV 작성 전문가. 포지셔닝 전략을 반영하여 ATS 최적화되고, 성과 중심으로 서술된 이력서를 작성한다.

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

## 확장 스킬

- `.agents/skills/ats-optimizer/SKILL.md`
- `.agents/skills/linkedin-seo/SKILL.md`
