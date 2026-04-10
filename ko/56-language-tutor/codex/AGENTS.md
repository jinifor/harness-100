# Language Tutor Harness Codex 지침

## 목적

- 이 디렉토리는 `Language Tutor Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/language-tutor/SKILL.md`
- 전문 agent: `.codex/agents/curriculum-designer.toml`, `.codex/agents/lesson-tutor.toml`, `.codex/agents/level-assessor.toml`, `.codex/agents/quiz-master.toml`, `.codex/agents/review-coach.toml`
- 확장 스킬: `.agents/skills/cefr-assessment/SKILL.md`, `.agents/skills/spaced-repetition/SKILL.md`

## 실행 원칙

- 전체 작업은 `language-tutor` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 외국어 학습을 위한 레벨 테스트, 커리큘럼, 레슨, 퀴즈, 복습 관리 에이전트 팀 하네스.
