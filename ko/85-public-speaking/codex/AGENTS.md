# Public Speaking Harness Codex 지침

## 목적

- 이 디렉토리는 `Public Speaking Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/public-speaking/SKILL.md`
- 전문 agent: `.codex/agents/audience-analyst.toml`, `.codex/agents/debate-preparer.toml`, `.codex/agents/qa-strategist.toml`, `.codex/agents/rehearsal-coach.toml`, `.codex/agents/speech-writer.toml`
- 확장 스킬: `.agents/skills/audience-engagement/SKILL.md`, `.agents/skills/rhetoric-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `public-speaking` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 퍼블릭스피킹 종합의 연설문→발표대본→토론준비서→Q&A예상답변→리허설가이드를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_audience_analysis.md` — 청중 분석 보고서
- `02_speech_script.md` — 연설문/발표 대본
- `03_debate_prep.md` — 토론 준비서
- `04_qa_playbook.md` — Q&A 예상 답변집
- `05_rehearsal_guide.md` — 리허설 가이드 및 검증 보고서
